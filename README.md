# AugGraffitti README
### EEE 598 MSA Assignment 1
Contributors: Irene Varughese, Jose Columbie
kdjfbsdbvjsdhfbjvshbdfkvsjhbdfv

___

This application consists of five activities: MainActivity.java, MapsActivity.java, PlaceActivity.java, CollectActivity.java, and GalleryActivity.java.

## MainActivity.java

The MainActivity class extends AppCompatActivity.

**Google API:** GoogleApiClient is a Google API provided in the Google Play services library. At ``` private GoogleApiClient singInGoogleApiClient;``` an instance of GoogleApiClient is created. 

**Check and register email:** Email registration in database is done at ``` public class BackGroundTask extends AsyncTask<String, Void, String>```. AsyncTask enables you to perform background operations on the UI thread. 

The ``` protected String doInBackground(String... strings)``` method performs the database check of the user's email through the ``` private String CheckInDatabase(String userEmail)``` method. This method uses HTTP POST requests to check the email. 

The result from this check is displayed through ``` protected void onPostExecute(String apiResult)``` method. 
 
**Initiate Activity:** ```protected void onCreate(Bundle savedInstanceState)``` is called when the activity is starting. onCreate calls ```setContentView(R.layout.activity_main);``` which starts up the activity UI. At ```public void onClick(View v)``` the Google sign-in button is displayed which in turn calls ```private void signIn()``` which calls ```startActivityForResult```.

**onActivity result:** This method is called when the activity exits. It gives you the *requestCode* you started with and *resultCode*, the integer returned by the child activity. 

**Handle *resultCode* and display welcome message:** ```private void handleSignInResult(GoogleSignInResult result)```  displays the authenticated or unauthenticated UI based on the *resultCode*. Upon successful sign-in, the MapsAcitivity is intitiated. 

## MapsActivity.java
 
The MapsActivity class implements the second screen of the app. 

**Initiate Activity:** ```protected void onCreate(Bundle savedInstanceState)``` is called when the activity is starting. onCreate cals ```setContentView(R.layout.activity_maps);``` in this activity which starts up the maps screen UI. 

**SupportMapFragment:** The SupportMapFragment fragment is a Google API that allows us to place a map in an application. The following fragment is added to activity_maps.xml file.
```R
<fragment xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:map="http://schemas.android.com/apk/res-auto"
								xmlns:tools="http://schemas.android.com/tools"
        android:id="@+id/map"
        android:name="com.google.android.gms.maps.SupportMapFragment"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context="com.example.javier.auggraffititest.MapsActivity" />
```
**Buttons:** The Map screen also shows the Collect, Gallery, and Score buttons.

**Signout:** The ```private void signOut()``` method implements the signout sequence and takes the user back to the Main activity. 

**Maps:** ```public void onMapReady(GoogleMap googleMap)``` is called when the map is ready to be used. 
It gets the handle to the ```GoogleMap``` object. 

**Location Services:** The methods ```public void onLocationChanged(Location location)```, ```public void onRequestPermissionsResult```, and ```public boolean checkLocationPermission()``` provide the necessary location services for the app. The method ```private String LookForTags(String userEmail, String loc_long, String loc_lat)``` looks for tags in a background thread.


## CollectActivity.java
 
The CollectActivity class implements the screen of the app that lets the user view and collect tags placed by artists. 

**Initiate Activity:** ```protected void onCreate(Bundle savedInstanceState)``` is called when the activity is starting. onCreate calls ```setContentView(R.layout.activity_main);``` which starts up the activity UI. The collect button is also initiated here. 

**Camera Operations and collect:** ```CameraManager``` is a system service manager for detecting, characterizing, and connecting to CameraDevices. This class is a client for the Camera service which manages the camera hardware. Methods ```createCameraPreview()```, ```updatePreview()```, ```collect()```, and ```closeCamera()``` performs the camera operations required for the Collect screen.

**Permissions:** Method ```onRequestPermissionsResult``` ensures required device permissions to use the camera.

## PlaceActivity.java
 
The PlaceActivity class implements the screen of the app that lets the user place tags at a certain geographical location. 

**Initiate Activity:** ```protected void onCreate(Bundle savedInstanceState)``` is called when the activity is starting. onCreate calls ```setContentView(R.layout.activity_main);``` which starts up the activity UI. The commit button is also initiated here.

**Orientations:** The SensorManager class is used to create an instance of the sensor service. This class provides access to azimuth and altitude information through the ```getOrientation()``` method.

**Camera Operations and commit:** ```CameraManager``` is a system service manager for detecting, characterizing, and connecting to CameraDevices. This class is a client for the Camera service which manages the camera hardware. Methods ```createCameraPreview()```, ```updatePreview()```, ```commit()```, and ```closeCamera()``` performs the camera operations required for the Place screen. 


## GalleryActivity.java
 
The GalleryActivity class implements the screen of the app that displays all the tags collected by the user. 

**Initiate Activity:** ```protected void onCreate(Bundle savedInstanceState)``` is called when the activity is starting. onCreate calls ```setContentView(R.layout.activity_main);``` which starts up the activity UI.

**Display images:** Methods ```getImages()``` opens POST connection and recieves the images in the Background thread. 





***

