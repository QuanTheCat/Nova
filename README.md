# Nova
//Code to be worked on between Levi and I, Planet rotation and Orbit being main focus.

//PLANET MOVEMENT

//NOTES: 
-Planets travel closer to "CenterPlanet" until they are at point (0,0) - 3/12/2017

//-----------------------------------------------------------ORBIT----------------------------------------------------------------//

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Orbit : MonoBehaviour {

	GameObject cube;
	public Transform center;
	public Vector3 axis = Vector3.up;
	public Vector3 desiredPosition;
	public float radius = 0;
	public float radiusSpeed = 0;
	public float rotationSpeed = 0f;

	void Start () {
		cube = GameObject.FindWithTag("CenterPlanet");
		center = cube.transform;
		transform.position = (transform.position - center.position).normalized * radius + center.position;
		radius = 0f;
	}

	void Update () {
		transform.RotateAround (center.position, axis, rotationSpeed * Time.deltaTime);
		desiredPosition = (transform.position - center.position).normalized * radius + center.position;
		transform.position = Vector3.MoveTowards(transform.position, desiredPosition, Time.deltaTime * radiusSpeed);
	}
}

//---------------------------------------------------------ROTATION---------------------------------------------------------------//

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Rotation : MonoBehaviour {

	public float rotationSpeed = 21.0f;
	// Use this for initialization
	void Start () {
		
	}
	
	// Update is called once per frame
	void Update () {
		transform.Rotate(Vector3.up, rotationSpeed * Time.deltaTime);

	}
}

//-------------------------------------------------------------END----------------------------------------------------------------//


