---
layout: post
title: 3D Printed Kinematic Mirror Mounts
---


The following is a guide on how to fabricate a low-cost alternative to commercial mirror mounts (around [$40 at their cheapest](https://www.thorlabs.com/thorproduct.cfm?partnumber=KM05)). Additionally, these allow you to customize your optics holder for any shape and size of optical element, which I found particularly useful as I was buying random surplus off of eBay. As a disclaimer, these mounts will have more thermal drift than anything commercial, and thus are less suitable for long-term experiments.

<figure style="float: right; margin-left: 20px; width:40%; height:auto;">
<img src="{{site.url}}/static/projects/mot/kinematic.png"/>
     <figcaption style="text-align:center; font-size: 13px; margin-top:-15px;">Image of kinematic mirror mount in CAD software</figcaption>
</figure>

<figure style="float: right; margin-left: 20px; width:40%; height:auto;">
<img src="{{site.url}}/static/projects/mot/mirror-final.jpg"/>
     <figcaption style="text-align:center; font-size: 13px; margin-top:-15px;">A fully assembled kinematic mirror mount</figcaption>
</figure>

# Theory

Kinematic mirror mounts are optomechanical devices ubiquitous in optical systems as they provide the ability to precisely tune the direction of a laser beam. This is achieved through the use of [**kinematic couplings**](https://en.wikipedia.org/wiki/Kinematic_coupling), from which these devices get their name.

The kinematic coupling fixtures constrain a baseplate and optics holder to be aligned in a fixed and highly repeatable manner, by ensuring that there are exactly six points of contact between the two (restricting the six mutual degrees of freedom between them). The method of affixing the baseplate and optics holder together is typically either via extension springs (most common) or magnets (but never bolts, as this would defeat the purpose of having only six points of contact).

<figure style="float: right; margin-left: 20px; width:40%; height:auto;">
<img src="{{site.url}}/static/projects/mot/kinematics.gif"/>
     <figcaption style="text-align:center; font-size: 13px; margin-top:-15px;">A visual demonstration of how a kinematic mirror mount works</figcaption>
</figure>

The six points of contact in a kinematic mirror mount are given by three round-tip screws through the baseplate that contact grooves in the optics holder. As the screws are driven, they push against one side of the optics holder, forcing it to tilt slightly in that direction. Thus, if the optics holder is holding a mirror with a laser beam incident on it, the output beam directionality will shift correspondingly. The springs holding the two pieces together provide a restoring force to un-tilt the optics holder if the screw is loosened.

# Fabrication

## Tools Required

* SLA 3D Printer (FDM possible but not recommended)
* Scotch Tape
* Epoxy

## Bill of Materials

### Purchase

* [M4 or 6-32 Bushings](https://www.amazon.com/Hilitchi-250-Pcs-Threaded-Embedment-Assortment/dp/B0784VYCYY/) x 3 (~$0.10 x 3)
* [M4 Ball-Tip Screws](https://www.amazon.com/Stainless-Steel-Socket-Spring-Screws/dp/B09D9H73S4/) x 3 (~$0.50 x 3)
* [1.5mm diameter, 6mm length dowel pins](https://www.mcmaster.com/93600A061/) x 6 (~$0.25 x 6)
* [0.125in diameter, 0.5in length extension springs](https://www.mcmaster.com/9654K942/) x 3 (~$0.80 x 3)
* [M3 bushing or nut](https://www.mcmaster.com/93090A636/) (~$0.02)  

### Print/Machine

* [Mirror Holder](https://github.com/m-k-S/openMOT/blob/master/cad/mirror_mounts/stl/26x20mm%20Mirror.stl) (modify this to your mirror dimensions)
* [Kinematic Mount](https://github.com/m-k-S/openMOT/blob/master/cad/mirror_mounts/stl/Kinematic%20Holder%20(M4%20Bushings).stl) (modify the bushing holes to your bushing dimensions)

<!-- <div id="model" style="width: 500px; height: 500px"> </div>
<script src="{{ site.url }}/public/js/three.min.js"></script>
<script src="{{ site.url }}/public/js/STLLoader.js"></script>
<script src="{{ site.url }}/public/js/OrbitControls.js"></script>

<script type="text/javascript">
function STLViewerEnable(classname) {
    var models = document.getElementsByClassName(classname);
    for (var i = 0; i < models.length; i++) {
        STLViewer(models[i], models[i].getAttribute("data-src"));
    }
}

function STLViewer(elementID, model) {
    var elem = document.getElementById(elementID);
    var renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
    var camera = new THREE.PerspectiveCamera(70, elem.clientWidth / elem.clientHeight, 1, 1000);
    renderer.setSize(elem.clientWidth, elem.clientHeight);
    elem.appendChild(renderer.domElement);

    window.addEventListener('resize', function () {
        renderer.setSize(elem.clientWidth, elem.clientHeight);
        camera.aspect = elem.clientWidth / elem.clientHeight;
        camera.updateProjectionMatrix();
    }, false);

    var controls = new THREE.OrbitControls(camera, renderer.domElement);
    controls.enableDamping = true;
    controls.rotateSpeed = 0.05;
    controls.dampingFactor = 0.1;
    controls.enableZoom = false;
    controls.enablePan = false;
    controls.autoRotate = true;
    controls.autoRotateSpeed = .75;

    var scene = new THREE.Scene();

    scene.add(new THREE.HemisphereLight(0xffffff, 0x080820, 1.5));

    (new THREE.STLLoader()).load(model, function (geometry) {
        var material = new THREE.MeshPhongMaterial({ color: 0xff5533, specular: 100, shininess: 100 });
        var mesh = new THREE.Mesh(geometry, material);
        scene.add(mesh);

        // Compute the middle
        var middle = new THREE.Vector3();
        geometry.computeBoundingBox();
        geometry.boundingBox.getCenter(middle);

        // Center it
        mesh.position.x = -1 * middle.x;
        mesh.position.y = -1 * middle.y;
        mesh.position.z = -1 * middle.z;

        // Pull the camera away as needed
        var largestDimension = Math.max(geometry.boundingBox.max.x,
            geometry.boundingBox.max.y, geometry.boundingBox.max.z)
        camera.position.z = largestDimension * 1.5;


        var animate = function () {
            requestAnimationFrame(animate);
            controls.update();
            renderer.render(scene, camera);
        }; animate();

    });
}
window.onload = function() {
    // STLViewer("model", "{{site.url}}/public/Kinematic Holder (M4 Bushings).stl");
    STLViewer("model", "https://github.com/m-k-S/openMOT/blob/master/cad/mirror_mounts/stl/Kinematic%20Holder%20(M4%20Bushings).stl");

    console.log("test");
}
</script> -->

## Assembly

I salvaged mirrors from a broken LCD projector (which, as an aside, is a great source of mirrors, prisms, lenses, and dichroics!), hence the random dimensions of 26x20mm. The mirror should slot into the mirror holder tightly enough to provide a tension fit to prevent any unwanted mechanical disturbance (you can modify the design to include a tension screw, or you can epoxy the mirror in, for extra sturdiness).

Next, epoxy your bushings into the holes in the kinematic mount. I used three M4 bushings for the adjustment screw holes, and an M3 bushing for the set screw hole to mount onto an optics post.

<figure style="float: right; margin-left: 20px; width:40%; height:auto;">
<img src="{{site.url}}/static/projects/mot/mirror-spring-tweezer.jpg"/>
     <figcaption style="text-align:center; font-size: 13px; margin-top:-15px;">Hook the spring on a dowel pin and pick the pin up with tweezers</figcaption>
</figure>

Then, thread a steel dowel pin through one of the loops on the end of a spring. Drop the dowel pin (with the spring attached) through the smaller hole in the kinematic mount, so that the dowel pin sits in the rectangular inset in the mount. Place a piece of scotch tape over the inset, so that the dowel pin and spring do not fall out. Do this for both insets. Then, flip the mirror mount over, and lift up the spring loop with a pair of tweezers. Use a second pair of tweezers to pick up another dowel pin and slide it through the spring loop. Do this for both spring slots, and then scotch tape over these holes as well.

<figure style="float: right; margin-left: 20px; width:40%; height:auto;">
<img src="{{site.url}}/static/projects/mot/mirror-tape-assembly.jpg"/>
     <figcaption style="text-align:center; font-size: 13px; margin-top:-15px;">Tape over the dowel pins so they do not fall out when you flip the device</figcaption>
</figure>

The final step is to screw your M4 ball-tip screws into the bushings until they sit in the triangular mounting insets in the mirror holder. Drive the screws far enough so that the springs are under tension, and the dowel pins will not fall out on their own. Then, the scotch tape can be removed, the mirror mount is fully assembled.

<figure style="float: right; margin-left: 20px; width:40%; height:auto;">
<img src="{{site.url}}/static/projects/mot/mirror-tweezer-assembly.jpg"/>
     <figcaption style="text-align:center; font-size: 13px; margin-top:-15px;">Lift the hook on the spring with one pair of tweezers and slide another dowel pin with the other pair</figcaption>
</figure>
