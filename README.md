QGIS:
Abstract
QGIS (Quantum Geographic Information System) is a free, open-source software that allows users to create, edit, visualize, analyze, and publish geospatial information. Create an interactive web map that displays the locations of victims, LoRa devices, and sensor devices. Active LoRa devices will be marked in green, while failed ones will be marked in red. We'll add layers using an XYZ layer, export the map using the QGIS2Web plugin, and then modify the exported code to include labels and buttons. When a user clicks on a node, a label will show a button that sends data to Grafana. Our main goal is to present this information visually for easy user understanding.
Step-by-Step Guide
Step 1: Install QGIS and QGIS2Web Plugin
Download and Install QGIS:
Go to the QGIS official website.
Download the latest version of QGIS suitable for your operating system (Windows, macOS, Linux).
Follow the installation instructions provided on the website for your OS.
Install QGIS2Web Plugin:
Open QGIS after installation.
Navigate to Plugins > Manage and Install Plugins.
In the Plugins dialog, search for "qgis2web".
Select the QGIS2Web plugin and click Install Plugin.
Step 2: Prepare Your Map in QGIS
Add Layers:
Open QGIS.
Load the layers you want to include in your web map.
Go to Layer > Add Layer.
Choose the appropriate type of layer (vector or raster or XYZ layers).
Load your shapefiles or other geographic data formats.
Open the Data Source Manager:
In QGIS, go to Layer in the top menu and select Data Source Manager.
Select XYZ Tiles:
In the Data Source Manager window, choose the XYZ option from the left sidebar.
Manage XYZ Connections:
In the XYZ Connections section, you can manage your tile connections. You will see options to New, Edit, and Remove connections.
Add a New XYZ Connection:
Click on the New button to add a new XYZ connection.
A new window will open where you can enter the connection details.
For Example:
Name: Give your new XYZ layer a name. In this case, it might be something descriptive like "Stamen Watercolor".
URL: Enter the URL template for the tile service. For example, in your screenshot, the URL is http://tile.stamen.com/watercolor/{z}/{x}/{y}.jpg. This URL will fetch the tiles from the Stamen Watercolor tile service.
Min. Zoom Level: Set the minimum zoom level. The default is usually 0.
Max. Zoom Level: Set the maximum zoom level. In your screenshot, it's set to 18, which is common for many tile services.
Referer: If needed, you can specify a referrer URL. This is usually optional.
Tile Resolution: Set the tile resolution if known, otherwise leave it as "Unknown (not scaled)".
Interpretation: Leave this as "Default" unless you need a specific interpretation for the tiles.

Save and Add the Layer:
After entering all the necessary details, click the Add button.
The XYZ tile layer will be added to your QGIS project and displayed in the Layers panel.
Step 3: Configure QGIS2Web Plugin
Open QGIS2Web Plugin:
Go to Web > qgis2web > Create web map.
Configure Export Options:
Layers and Appearance:
Select the layers you want to include in the web map.
Export Format:
Choose between Leaflet or OpenLayers (Leaflet is commonly used and user-friendly).
Leaflet allows you to customise the map and add functionalities in the map by using Javascript.
Map Options:
Extent: Set the extent of the map to cover your area of interest.
Controls: Configure controls like zoom, scale, search, and live location.
Preview:
Use the preview pane to see how your web map will look.
Step 4: Export the Web Map
Export Map:
Click Export.
Choose the directory where you want to save the web map files.
The plugin will generate HTML, JavaScript, and CSS files required for your web map.
Step 5: Access the Web Map
Local Preview:
Open the exported HTML file in a web browser to preview your web map locally.
Step 6: Customize the Map
Edit HTML/JavaScript/CSS:
For advanced customizations, you can manually edit the exported HTML, JavaScript, and CSS files.
Add custom scripts or styles to enhance functionality and appearance.
Customizations
1. Custom Icon Function
Purpose: This function creates custom icons for the map markers. It specifies the image URL for the icon, its size, the point of the icon that should be anchored to the marker's location, and the point from which a popup should open.
2. Defining Colors and Places
Colours: A JavaScript object called colours is used to store the status of various LoRa nodes. Each key in the object corresponds to a node ID, and the value indicates whether the node is active (1) or failed (0).
Places: An array called places is used to define the coordinates, names, and custom icon URLs for different locations. Each entry in the array represents a location with its ID, name, latitude, longitude, and icon URL.
3. Sending Data to Backend
Function: A function sendDataToBackend is defined to send data to the backend server when a marker is clicked. This function uses the Fetch API to send a POST request with the marker's ID, name, latitude, and longitude as a JSON object.
Usage: When a user clicks on a marker, this function is triggered to send the marker's details to a specified backend URL.
4. Periodic Data Update
Set Interval: A setInterval function is used to periodically fetch updated data from the backend server. This is done every 30 seconds.
Fetching Data: The function fetches data from the backend URL and updates the colours object based on the fetched data.
Updating Markers: After updating the colours object, the function iterates over the places array and updates the markers on the map. It sets the marker's icon and name based on the current status (active or failed) of each node.
5. Adding Markers to the Map
Function to Add Markers: A function addMarker is defined to add markers to the map. It takes the marker's ID, latitude, longitude, name, and icon URL as arguments.
Creating Popups: For each marker, a popup is created with the location's name and a button. When the button is clicked, it triggers the sendDataToBackend function to send the marker's details to the backend.
Custom Icons: The function uses the createCustomIcon function to create a custom icon for each marker based on the provided icon URL.
6. Module Export
Custom Leaflet Control: A custom Leaflet control is extended to include search functionality. This control allows users to search for locations on the map and provides various customization options for the search behaviour.
URL Parsing: A method findsearch is included to extract a location from the URL and trigger a geocode search. This helps in locating and highlighting specific places on the map based on the URL parameters.
7. Add Labels and Buttons:
Modify the exported JavaScript code to add labels for victim locations and LoRa devices.
When a user clicks on a node, a label should show a button.
Configure the button to send data to Grafana when clicked.
