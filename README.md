<!DOCTYPE html>
<html>
<head>
    <title>Квартира</title>
    <script src="https://cdn.jsdelivr.net/npm/three@0.132.2/build/three.min.js"></script>
</head>
<body>
    <script>
        var scene = new THREE.Scene();
        var camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        camera.position.z = 5;
        var renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);
        var wallGeometry = new THREE.BoxGeometry(0.5, 1, 0.1);
        var wallMaterial = new THREE.MeshBasicMaterial({ color: 0x808080 });
        var wall = new THREE.Mesh(wallGeometry, wallMaterial);
        scene.add(wall);
        document.addEventListener('touchmove', onDocumentTouchMove, false);
        function onDocumentTouchMove(event) {
            wall.scale.set(event.touches[0].clientX / window.innerWidth, event.touches[0].clientY / window.innerHeight, 1);
        }
        function animate() {
            requestAnimationFrame(animate);
            renderer.render(scene, camera);
        }
        animate();
    </script>
</body>
</html>
