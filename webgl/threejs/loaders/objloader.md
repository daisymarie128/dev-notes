## Object Loader

Template code for loading in `.obj` files.

```javascript
const manager = new THREE.LoadingManager();
manager.onProgress = (item, loaded, total) => {
	console.log( item, loaded, total );
};

const texture = new THREE.Texture();
onProgress = (xhr) => {
	if ( xhr.lengthComputable ) {
		const percentComplete = xhr.loaded / xhr.total * 100;
		console.log( Math.round(percentComplete, 2) + '% downloaded' );
	}
};

onError = (xhr) => {
  console.log('error loading');
};

const loader = new THREE.ImageLoader(manager);
loader.load( 'textures/example.jpg', (image) => {
	texture.image = image;
	texture.needsUpdate = true;
});

// load in the obj model
const loader = new THREE.OBJLoader(manager);
loader.load( '../filelocation.obj', (object) => {
	object.traverse( function (child) {
		if ( child instanceof THREE.Mesh ) {
			child.material.map = texture;
		}
	} );

	scene.add( object );
}, onProgress, onError );
```
