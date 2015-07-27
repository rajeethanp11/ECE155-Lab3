package ca.uwaterloo.Lab3_201_11;

//import java.util.Arrays;

import java.util.Arrays;

import mapper.MapLoader;
import mapper.MapView;
import mapper.NavigationalMap;

//import mapper.MapLoader;
//import mapper.MapView;
//import mapper.NavigationalMap;

//import ca.uwaterloo.Lab1_201_11.MagneticFieldSensorEventListener;
//import ca.uwaterloo.Lab2_201_11.LightSensorEventListener;
import ca.uwaterloo.Lab3_201_11.LineGraphView;
import ca.uwaterloo.Lab3_201_11.MagneticFieldSensorEventListener;
import ca.uwaterloo.Lab3_201_11.R;
//import ca.uwaterloo.Lab2_201_11.RotationVector;
import ca.uwaterloo.Lab3_201_11.accelerometer;

import android.support.v7.app.ActionBarActivity;
import android.support.v7.app.ActionBar;
import android.support.v4.app.Fragment;
import android.graphics.Color;
import android.hardware.Sensor;
import android.hardware.SensorEvent;
import android.hardware.SensorEventListener;
import android.hardware.SensorManager;
import android.os.Bundle;
import android.view.ContextMenu;
import android.view.ContextMenu.ContextMenuInfo;
import android.view.Gravity;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;
import android.widget.LinearLayout;
import android.widget.TextView;
import android.os.Build;



import android.support.v7.app.ActionBarActivity;
import android.support.v7.app.ActionBar;
import android.support.v4.app.Fragment;
import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.os.Build;

public class MainActivity extends ActionBarActivity {
		
	static MapView mview;
	//Code entered as per lab manual instructions
	
	@Override
	public void onCreateContextMenu ( ContextMenu menu , View v, ContextMenuInfo menuInfo ) {
	super . onCreateContextMenu (menu , v, menuInfo );
	mview. onCreateContextMenu (menu , v, menuInfo );
	}
	
	@Override
	public boolean onContextItemSelected ( MenuItem item ) {
	return super . onContextItemSelected ( item ) || mview . onContextItemSelected ( item );
    }
	
	//Code entered as per lab manual instructions
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		
		//Declaring new MapView object 
		
		mview = new MapView(getApplicationContext(),900,650,20,20);
		registerForContextMenu(mview);
		NavigationalMap map = MapLoader.loadMap(getExternalFilesDir(null), "E2-3344.svg");
		mview.setMap(map);
		
		//Declaring new MapView object
		
		if (savedInstanceState == null) {
			getSupportFragmentManager().beginTransaction()
					.add(R.id.container, new PlaceholderFragment()).commit();
		}
	}

	@Override
	public boolean onCreateOptionsMenu(Menu menu) {
		// Inflate the menu; this adds items to the action bar if it is present.
		getMenuInflater().inflate(R.menu.main, menu);
		return true;
	}

	@Override
	public boolean onOptionsItemSelected(MenuItem item) {
		// Handle action bar item clicks here. The action bar will
		// automatically handle clicks on the Home/Up button, so long
		// as you specify a parent activity in AndroidManifest.xml.
		int id = item.getItemId();
		if (id == R.id.action_settings) {
			return true;
		}
		return super.onOptionsItemSelected(item);
	}

	/**
	 * A placeholder fragment containing a simple view.
	 */
	public static class PlaceholderFragment extends Fragment {
		
		public PlaceholderFragment() {
		}

		@Override
		public View onCreateView(LayoutInflater inflater, ViewGroup container,
				Bundle savedInstanceState) {
			View rootView = inflater.inflate(R.layout.fragment_main, container,
					false);
			LinearLayout layout = (LinearLayout) rootView.findViewById(R.id.label2);
	 		
			
			//Rotation Matrix
			
			float[] Rotation = new float[3];
			
           //RotationMatrix
			
			//Adding MapView object to the view
			
			layout.addView(mview);
			
			//Adding MapView object to the view
			
			            //sets layout to vertical
			            
			            layout.setOrientation(LinearLayout.VERTICAL);
			           
			            //LineGraphView object creation
			            
			            LineGraphView graph = new LineGraphView(rootView.getContext(),100,Arrays.asList("x","y","z"));
			            layout.addView(graph);
			            graph.setVisibility(View.VISIBLE);
			            
			            LineGraphView graph2 = new LineGraphView(rootView.getContext(),100,Arrays.asList("x","y","z"));
			           // layout.addView(graph2);
			           // graph.setVisibility(View.VISIBLE);
			            
			            //second graph being added to the view to be used in linear acceleration
			            /*
			            LineGraphView anothergraph = new LineGraphView(rootView.getContext(),100,Arrays.asList("x","y","z"));
			            layout.addView(graph);
			            graph.setVisibility(View.VISIBLE);
			            */
			            //second graph being added to the view to be used in linear acceleration
			            //Redundant code Please remove afterwards
			            //Redundant code from Lab1
			            
			            //TextView tv = (TextView) rootView.findViewById(R.id.label1);
						//tv.setText("I’ve replaced the label!");
						//TextView tv1 = new TextView(rootView.getContext());
						//tv1.setText("Example Text");
						//tv1.findViewById(R.id.label2);
						//layout.addView(tv1);
						
			            //Redundant code Please remove afterwards
			            
			            //Declares Sensor  
						
					    SensorManager sensorManager = (SensorManager) rootView.getContext().getSystemService(SENSOR_SERVICE);
					            
			            //Accelerometer Starts
				
					    //new variable creation for lab2
						
						//TextView orientationDegree = new TextView(rootView.getContext());
						//orientationDegree.setText("orientation array value");
						//layout.addView(orientationDegree);
					    
					    TextView accelWalk = new TextView(rootView.getContext());
						accelWalk.setText("output for steps");
						layout.addView(accelWalk);
						
						TextView northSouthWalk = new TextView(rootView.getContext());
						northSouthWalk.setText("ns displacement");
						layout.addView(northSouthWalk);
						
						TextView eastWestWalk = new TextView(rootView.getContext());
						eastWestWalk.setText("ew displacement");
						layout.addView(eastWestWalk);
			            
						TextView testtext = new TextView(rootView.getContext());
					    testtext.setText("sd");
					    layout.addView(testtext);
						//new variable creation for lab2 
						
			            Sensor AccelerometerSensor = sensorManager.getDefaultSensor(Sensor.TYPE_LINEAR_ACCELERATION);
			            SensorEventListener a = new accelerometer(accelWalk, graph, northSouthWalk, eastWestWalk, Rotation, testtext/*orientationDegree*/);
			            sensorManager.registerListener(a, AccelerometerSensor, SensorManager.SENSOR_DELAY_FASTEST);
			            
			            //Accelerometer ends
			            
			            //BACK TO THE OLD ACCELERATION
			            //ACCELEROMETER
			            
			            Sensor AccelerometerSensorL = sensorManager.getDefaultSensor(Sensor.TYPE_ACCELEROMETER);
			            SensorEventListener al = new accelerometerEventListener(Rotation);
			            sensorManager.registerListener(al, AccelerometerSensorL, SensorManager.SENSOR_DELAY_NORMAL);
			            
			            //ACCELEROMETER
			            //BACK TO THE OLD ACCELERATION
			            //MagneticFieldSensor Starts
			            
			            TextView magneticFieldVariable = new TextView(rootView.getContext());
			            magneticFieldVariable.setTextColor(Color.parseColor("#FF0000"));
			            magneticFieldVariable.setText("---   MAGNETIC FIELD VALUES   ---");
			            layout.addView(magneticFieldVariable);
			            
			            TextView magneticOrientationOutput = new TextView(rootView.getContext());
			            magneticOrientationOutput.setText("Test test");
			            layout.addView(magneticOrientationOutput);
			         
			            			            
			            Sensor magneticFieldSensor = sensorManager.getDefaultSensor(Sensor.TYPE_MAGNETIC_FIELD);
			            SensorEventListener m1 = new MagneticFieldSensorEventListener(magneticFieldVariable, magneticOrientationOutput,Rotation, graph2);
			            sensorManager.registerListener(m1, magneticFieldSensor, SensorManager.SENSOR_DELAY_NORMAL);
			            
	                    
			            //Clear Button for NS STEPS AND EW STEPS
			            
			            Button clearNSEW = new Button(rootView.getContext());
			            clearNSEW.setTextColor(Color.parseColor("#FF0000"));//Changed to red to differentiate
			            clearNSEW.setText("RESET NSEW DISPL");
			            layout.addView(clearNSEW);
			            
			            clearNSEW.setOnClickListener(new View.OnClickListener() {
							
							@Override
							public void onClick(View v) {
								ca.uwaterloo.Lab3_201_11.accelerometer.northSouthStepsTaken = 0;
								ca.uwaterloo.Lab3_201_11.accelerometer.eastWestStepsTaken = 0;
							    ca.uwaterloo.Lab3_201_11.accelerometer.totalDisplacementOutput = 0;
							}
						});
			            
			            //Clear Button for NS STEPS AND EW STEPS
			            
			            //Reset Button for Resetting the number of Steps to zero
			            
			          Button clear = new Button(rootView.getContext()); //Creates an object which is of type button 
			          clear.setTextColor(Color.parseColor("#0000CC")); //text in blue colour
			          clear.setText("RESET STEPS");
			          layout.addView(clear);
			          
			          clear.setOnClickListener(new View.OnClickListener() {
			              public void onClick(View v) {
			                  
			            	  // Perform action on click
			            	  // Complete reset of values
			            	  // stepsTaken set to zero
			            	  // Syntax obtained from android documentation
			            	
			            	  ca.uwaterloo.Lab3_201_11.accelerometer.stepsTaken = 0;
			              }
			          });
			          
			           return rootView;
			           
		}
	}
}
class MagneticFieldSensorEventListener implements SensorEventListener {
	TextView magneticOutput;
	TextView orientationOutput; 
	LineGraphView graphtest_second;
	static float[] magneticFieldValues = new float[3];
	
	float[] R = new float[9];
	float[] I = new float[9];
	float testv;
	float[] gravityvaluesfromaccelerometer;
	static float[] orientationArray = new float[3];
	
	static float[] getOrientationArray()
	{
		return orientationArray;
	}
	
	public MagneticFieldSensorEventListener(TextView outputArgument, TextView orientationArgument, float[] gravityArgument, LineGraphView graphCopy) {
		
		magneticOutput = outputArgument;
		orientationOutput = orientationArgument;
		graphtest_second = graphCopy;
		gravityvaluesfromaccelerometer = gravityArgument;
	
	}
	
	public void onAccuracyChanged(Sensor s, int i) {}
	
	public void onSensorChanged(SensorEvent se) {
	  if(se.sensor.getType() == Sensor.TYPE_MAGNETIC_FIELD) {
		 
		  magneticFieldValues[0] = se.values[0];
		  magneticFieldValues[1] = se.values[1];
		  magneticFieldValues[2] = se.values[2];
		 
		 
		  SensorManager.getRotationMatrix(R, I, gravityvaluesfromaccelerometer, magneticFieldValues); //Change to se.values after testing
		  //Source : Android Documentation
		  /*
		   * Computes the inclination matrix I as well as the rotation matrix R transforming a vector from the device coordinate system to the world's coordinate system which is defined as a direct orthonormal basis, where: 
              X is defined as the vector product Y.Z (It is tangential to the ground at the device's current location and roughly points East). 
              Y is tangential to the ground at the device's current location and points towards the magnetic North Pole. 
              Z points towards the sky and is perpendicular to the ground. 
		   */
		  
		  orientationArray = SensorManager.getOrientation(R,orientationArray);
		  
		  //DEbugging
		  //output.setText("Hello" + gravityvaluesfromaccelerometer[0]);
		  //DEbugging
		  
		  //Gets the values stored in R and puts them in the orientationArray.
		  //Thus the orientationArray array gets populated with the values of R
		  //Just for reference [0] is around z axis, [1] is around x axis, [2] is around y axis 
		 // testv = (float) ((orientationArray[1]*180)/(Math.PI));
		  orientationOutput.setText("Orientation is " + "X : " + orientationArray[0] + ", Y : " + orientationArray[1] + ", Z : " + orientationArray[2]);
		  magneticOutput.setText("Magnetic field values are " + "X : " + magneticFieldValues[0] + ", Y : " + magneticFieldValues[1] + ", Z : " + magneticFieldValues[2]);
	
		  //graphtest_second.addPoint(orientationArray);
		  
	}
	}

}


class accelerometerEventListener implements SensorEventListener {
		
	static float[] gravityvaluesfromaccelerometer;
	
	//Don't know why this function exists ... Probably i had put it in for debugging
	
	static float[] getgravityvaluesfromaccelerometer()
	{
		return gravityvaluesfromaccelerometer;
	}
	//Don't know why this function exists ... Probably i had put it in for debugging
	
	public accelerometerEventListener(float[] gravityargument) {
       
		gravityvaluesfromaccelerometer = gravityargument;
		
	}
	
	public void onAccuracyChanged(Sensor S, int i) {}
	
	public void onSensorChanged(SensorEvent se) {
		
		if(se.sensor.getType() == Sensor.TYPE_ACCELEROMETER) {
			
			gravityvaluesfromaccelerometer[0] = se.values[0];
			gravityvaluesfromaccelerometer[1] = se.values[1];
			gravityvaluesfromaccelerometer[2] = se.values[2];
		}
		
	}
	
}




class accelerometer implements SensorEventListener {
	
	
	// Declaration of two variables,one to count the number of steps
	// and the other to use in the state machine algorithm so it helps
	// us clearly define what a step is
	
    public static int positionVariableForSteps = 0;
	public static int stepsTaken = 0;
	public static double northSouthStepsTaken = 0;
	public static double eastWestStepsTaken = 0;
	
	float[] orientationArrayCopy;
	float[] gravityvaluesfromaccelerometer;	
	
	TextView stepsOutput;
	TextView degreeOutputDegrees;
	TextView northSouthStepsOutput;
	TextView eastWestStepsOutput;
	TextView totalDisplacementOutputText;
	public static double totalDisplacementOutput = 0;
	LineGraphView graphtest;
	
	public accelerometer(TextView accelWalk, LineGraphView graphCopy, TextView northSouthDirection, TextView eastWestDirection, float[] gravity, TextView testCopy/*TextView degree*/) {
		
		stepsOutput = accelWalk;
		graphtest = graphCopy;
		northSouthStepsOutput = northSouthDirection;
		eastWestStepsOutput = eastWestDirection;
		gravityvaluesfromaccelerometer = gravity;
		totalDisplacementOutputText = testCopy;
		//degreeOutputDegrees = degree;
		
	}
	
	public void onAccuracyChanged(Sensor S, int i) {}
	
	public void onSensorChanged(SensorEvent se) {
		
		    //Putting the values of "se.values" array into a float array in order 
		    //to pass it to the addPoint method of LineGraphView.java which takes in a 
		    //float array as an argument
		
		    float[] statemachinevalues = new float[se.values.length];
		 
		    if(se.sensor.getType() == Sensor.TYPE_LINEAR_ACCELERATION) {
			
			//algorithm for low pass filter 
			
			statemachinevalues = se.values;
			
			// Forcibly set the x and z axis values to zero as we're not using it
			// This is done as a precautionary measure so as to maintain accuracy 
			// in our preferred axis of choice(in this case the Y-axis) so as to 
			// count the steps
			
			statemachinevalues[0] = 0;
			statemachinevalues[2] = 0;
			
			
			//Gets the values from the magnetic field sensor
			//orientationArrayCopy = MagneticFieldSensorEventListener.getOrientationArray(); 
			//Gets the values from the magnetic field sensor
			
			
			// Only using the y-axis.
			// The z-axis and the x-axis are not used and hence their values are 
			// immediately and forcibly set to zero
			
			
			// Filter algorithm to filter out the noise as given per the Lab Manual
			
			statemachinevalues[1] += (se.values[1] - statemachinevalues[1]) / 2.5; //arbitrary constant for c
			
			// The value of the Constant "C" is arbitary as long as it is sufficently low enough
			// For optimal results one might use the value of C between 2 and 3
					
			
			// Each step that you take consists of an increasing function
			// So every step you take consists of the function going from a 
			// Decreasing value to an increasing value and back to a decreasing value
			// So it basically means that in order for the step to be counted
			// One would have to calculate the the fall state, the peak state 
			// and the rise state (and possibly the small negative value that 
			// arises when we finish taking one step) and use those values
			// to approximate our state machine algorithm so that it knows	
			// when a step is to be registered. 
			
			// Rising State of the curve
			if (positionVariableForSteps == 0 && statemachinevalues[1] >= 0.1 && statemachinevalues[1] <= 0.2){
				positionVariableForSteps = 1;				
			}
			
			// If the filtered value is indeed in the rising state then 
			// the "positionVariableForSteps" is incremented by 1 so as to 
			// let us know that the person has just begun to take a step
			
			// Peak State of the curve
			if (positionVariableForSteps == 1 && statemachinevalues[1] >= 0.6 && statemachinevalues[1] <= 1.5){
				positionVariableForSteps = 2; 			
			}
			
			// If the filtered value is indeed in the peak state then 
			// the "positionVariableForSteps" is incremented by 1 so as to 
			// let us know that the person is in the middle of taking a step
			
			// Falling state of the curve
			if (positionVariableForSteps == 2 && statemachinevalues[1] >= 0.6 && statemachinevalues[1] <= 1.2){
				positionVariableForSteps = 3;				
			}
			
			// If the filtered value is indeed in the falling state then 
			// the "positionVariableForSteps" is incremented by 1 so as to 
			// let us know that the person has finished taking a step
			
			/*
			 * 
			 * --->  FALSE POSITIVE VALUES TO BE NOTED <----
			//Small Negative State that occurs while walking
			
			if (positionVariableForSteps == 2 && statemachinevalues[1] >= 0 && statemachinevalues[1] <= 0.1){
				positionVariableForSteps = 4;
			}
			
			*FALSE POSITIVE VALUES TO BE NOTED
			*/	
			
			// Now if the "positionVariableForSteps" has a value of three then
			// we know for sure that a step has been completed and now the next 
			// thing to do would be to count the step just taken
			// Hence we increment the "stepsTaken" variable by 1
			
			if (positionVariableForSteps == 3){
				
				stepsTaken++;
				
				//Gets the values from the magnetic field sensor
				orientationArrayCopy = MagneticFieldSensorEventListener.getOrientationArray(); 
				//Gets the values from the magnetic field sensor
				
				northSouthStepsTaken = northSouthStepsTaken + Math.cos(orientationArrayCopy[0]);
				eastWestStepsTaken = eastWestStepsTaken + Math.sin(orientationArrayCopy[0]);		
				totalDisplacementOutput = Math.sqrt(Math.pow(northSouthStepsTaken, 2) + Math.pow(eastWestStepsTaken, 2));
				positionVariableForSteps = 0;   
			    
			}
			//totalDisplacementOutput = 0;
			// We also reset the "positionVariableForSteps" to zero
            // because this serves as an iterative loop and we have to 
			// start checking if the next step has been taken or not
			
			stepsOutput.setText("\n Steps Counter : " + stepsTaken + "\n");
			
			//Displays ns and ew directions for steps
			
			northSouthStepsOutput.setText("North-South Steps Counter : " + northSouthStepsTaken + "\n");
			eastWestStepsOutput.setText("East-West Steps Counter : " + eastWestStepsTaken + "\n");
			totalDisplacementOutputText.setText("Total-displacement : " + totalDisplacementOutput);
			//degreeOutputDegrees.setText("Azimuth value in degrees " + (orientationArrayCopy[0]));
			//Displays ns and ew directions for steps
		
			
			// Centre align the output
			// Source : Android Documentation TextView.setGravity
		
//			output.setGravity(Gravity.CENTER_HORIZONTAL);
			
			// adds the respective points to the graph using the addPoint method
			// We can actually see from the graph the corresponding state machine 
			// values when we are in the process of taking a step
			// ie: namely rise state, peak state and fall state
			
			graphtest.addPoint(statemachinevalues);		
		
			
		}	
	}
	
	
}



