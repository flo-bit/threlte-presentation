<script>
	import MySlide from '$lib/MySlide.svelte';
	import { Code } from '@animotion/core';
	import WebGlScene from './WebGLScene.svelte';
	import { Canvas } from '@threlte/core';
	import DemoSlide from '$lib/DemoSlide.svelte';
</script>

<DemoSlide title="WebGL cube">
	<div class="max-h-full overflow-y-scroll p-16 text-4xl pt-32">
		<Code
			lang="js"
			theme="github-light"
            class="rounded-md p-4"
			code={`// Get the canvas element and its drawing context
        const canvas = document.getElementById('webglCanvas');
        const gl = canvas.getContext('webgl');

        // Check whether WebGL is available
        if (!gl) {
            alert('WebGL is not supported on your browser.');
            throw new Error('WebGL not supported');
        }

        // Vertex shader program
        const vsSource = \`
            attribute vec4 aVertexPosition;
            uniform mat4 uModelViewMatrix;
            uniform mat4 uProjectionMatrix;
            void main() {
                gl_Position = uProjectionMatrix * uModelViewMatrix * aVertexPosition;
            }
        \`;

        // Fragment shader program
        const fsSource = \`
            void main() {
                gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // red color
            }
        \`;

        // Initialize shaders
        function initShaderProgram(gl, vsSource, fsSource) {
            const vertexShader = loadShader(gl, gl.VERTEX_SHADER, vsSource);
            const fragmentShader = loadShader(gl, gl.FRAGMENT_SHADER, fsSource);

            // Create the shader program
            const shaderProgram = gl.createProgram();
            gl.attachShader(shaderProgram, vertexShader);
            gl.attachShader(shaderProgram, fragmentShader);
            gl.linkProgram(shaderProgram);

            // Check for successful program creation
            if (!gl.getProgramParameter(shaderProgram, gl.LINK_STATUS)) {
                alert('Unable to initialize the shader program: ' + gl.getProgramInfoLog(shaderProgram));
                return null;
            }
            return shaderProgram;
        }

        // Creates a shader of the given type, uploads the source and compiles it.
        function loadShader(gl, type, source) {
            const shader = gl.createShader(type);
            gl.shaderSource(shader, source);
            gl.compileShader(shader);

            // Check if shader compilation was successful
            if (!gl.getShaderParameter(shader, gl.COMPILE_STATUS)) {
                alert('An error occurred compiling the shaders: ' + gl.getShaderInfoLog(shader));
                gl.deleteShader(shader);
                return null;
            }
            return shader;
        }

        const shaderProgram = initShaderProgram(gl, vsSource, fsSource);

        // Collect all the info needed to use the shader program.
        const programInfo = {
            program: shaderProgram,
            attribLocations: {
                vertexPosition: gl.getAttribLocation(shaderProgram, 'aVertexPosition'),
            },
            uniformLocations: {
                projectionMatrix: gl.getUniformLocation(shaderProgram, 'uProjectionMatrix'),
                modelViewMatrix: gl.getUniformLocation(shaderProgram, 'uModelViewMatrix'),
            },
        };

        // Build the cube
        function initBuffers(gl) {
            const positionBuffer = gl.createBuffer();
            gl.bindBuffer(gl.ARRAY_BUFFER, positionBuffer);

            // An array of positions for the cube
            const positions = [
                // Front face
                -1.0, -1.0,  1.0,
                 1.0, -1.0,  1.0,
                 1.0,  1.0,  1.0,
                -1.0,  1.0,  1.0,
                
                // Back face
                -1.0, -1.0, -1.0,
                -1.0,  1.0, -1.0,
                 1.0,  1.0, -1.0,
                 1.0, -1.0, -1.0,

                // Top face
                -1.0,  1.0, -1.0,
                -1.0,  1.0,  1.0,
                 1.0,  1.0,  1.0,
                 1.0,  1.0, -1.0,

                // Bottom face
                -1.0, -1.0, -1.0,
                 1.0, -1.0, -1.0,
                 1.0, -1.0,  1.0,
                -1.0, -1.0,  1.0,

                // Right face
                 1.0, -1.0, -1.0,
                 1.0,  1.0, -1.0,
                 1.0,  1.0,  1.0,
                 1.0, -1.0,  1.0,

                // Left face
                -1.0, -1.0, -1.0,
                -1.0, -1.0,  1.0,
                -1.0,  1.0,  1.0,
                -1.0,  1.0, -1.0,
            ];

            // Pass the list of positions into WebGL to build the shape
            gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(positions), gl.STATIC_DRAW);

            const indexBuffer = gl.createBuffer();
            gl.bindBuffer(gl.ELEMENT_ARRAY_BUFFER, indexBuffer);

            // This array defines each face as two triangles, using the indices
            // into the vertex array to specify each triangle's position.
            const indices = [
                0, 1, 2,      0, 2, 3,    // front
                4, 5, 6,      4, 6, 7,    // back
                8, 9, 10,     8, 10, 11,  // top
                12, 13, 14,   12, 14, 15, // bottom
                16, 17, 18,   16, 18, 19, // right
                20, 21, 22,   20, 22, 23  // left
            ];

            // Send the element array to WebGL
            gl.bufferData(gl.ELEMENT_ARRAY_BUFFER, new Uint16Array(indices), gl.STATIC_DRAW);

            return {
                position: positionBuffer,
                indices: indexBuffer,
            };
        }

        const buffers = initBuffers(gl);

        // Draw the scene
        function drawScene(gl, programInfo, buffers) {
            gl.clearColor(0.0, 0.0, 0.0, 1.0);  // Clear to black, fully opaque
            gl.clearDepth(1.0);                 // Clear everything
            gl.enable(gl.DEPTH_TEST);           // Enable depth testing
            gl.depthFunc(gl.LEQUAL);            // Near things obscure far things

            // Clear the canvas before drawing on it
            gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT);

            // Create a perspective matrix, a special matrix that is
            // used to simulate the distortion of perspective in a camera.
            // Our field of view is 45 degrees, with a width/height
            // ratio that matches the display size of the canvas
            // and we only want to see objects between 0.1 units
            // and 100 units away from the camera.
            const fieldOfView = 45 * Math.PI / 180;   // in radians
            const aspect = gl.canvas.clientWidth / gl.canvas.clientHeight;
            const zNear = 0.1;
            const zFar = 100.0;
            const projectionMatrix = mat4.create();

            // note: glmatrix.js always has the first argument
            // as the destination to receive the result.
            mat4.perspective(projectionMatrix,
                             fieldOfView,
                             aspect,
                             zNear,
                             zFar);

            // Set the drawing position to the "identity" point, which is
            // the center of the scene.
            const modelViewMatrix = mat4.create();

            // Now move the drawing position a bit to where we want to
            // start drawing the square.
            mat4.translate(modelViewMatrix,     // destination matrix
                           modelViewMatrix,     // matrix to translate
                           [-0.0, 0.0, -6.0]);  // amount to translate

            // Tell WebGL how to pull out the positions from the position
            // buffer into the vertexPosition attribute.
            gl.bindBuffer(gl.ARRAY_BUFFER, buffers.position);
            gl.vertexAttribPointer(
                programInfo.attribLocations.vertexPosition,
                3,          // Number of components per vertex position (vec3)
                gl.FLOAT,   // Data type
                false,      // Normalize
                0,          // Stride
                0           // Offset
            );
            gl.enableVertexAttribArray(
                programInfo.attribLocations.vertexPosition
            );

            // Tell WebGL which indices to use to index the vertices
            gl.bindBuffer(gl.ELEMENT_ARRAY_BUFFER, buffers.indices);

            // Tell WebGL to use our program when drawing
            gl.useProgram(programInfo.program);

            // Set the shader uniforms
            gl.uniformMatrix4fv(
                programInfo.uniformLocations.projectionMatrix,
                false,
                projectionMatrix);
            gl.uniformMatrix4fv(
                programInfo.uniformLocations.modelViewMatrix,
                false,
                modelViewMatrix);

            {
                const vertexCount = 36;
                const type = gl.UNSIGNED_SHORT;
                const offset = 0;
                gl.drawElements(gl.TRIANGLES, vertexCount, type, offset);
            }
        }

        drawScene(gl, programInfo, buffers);`}
		/>
	</div>
	<div class="w-1/2 h-full absolute top-0 bottom-0 right-0">
		<Canvas>
			<WebGlScene />
		</Canvas>
	</div>
</DemoSlide>
