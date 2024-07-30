Interactive Web Map with QGIS and QGIS2Web
Abstract
This project involves creating an interactive web map to visualize the locations of victims, LoRa devices, and sensor devices. Active LoRa devices are marked in green, while failed ones are marked in red. We will add layers using XYZ tiles, export the map using the QGIS2Web plugin, and modify the exported code to include labels and buttons. The goal is to present this information visually for easy user understanding.

Step-by-Step Guide
Step 1: Install QGIS and QGIS2Web Plugin
Download and Install QGIS:

Go to the QGIS official website.
Download the latest version suitable for your operating system (Windows, macOS, Linux).
Follow the installation instructions provided on the website.
Install QGIS2Web Plugin:

Open QGIS.
Navigate to Plugins > Manage and Install Plugins.
Search for "qgis2web" in the Plugins dialog.
Select the QGIS2Web plugin and click Install Plugin.
Step 2: Prepare Your Map in QGIS
Add Layers:

Open QGIS.
Load the layers you want to include in your web map.
Go to Layer > Add Layer and choose the appropriate type (vector, raster, or XYZ layers).
Load your shapefiles or other geographic data formats.
Open the Data Source Manager:

Go to Layer > Data Source Manager.
Choose the XYZ option from the left sidebar.
Manage XYZ Connections:

In the XYZ Connections section, manage your tile connections (New, Edit, Remove).
Click New to add a new XYZ connection.
Enter the connection details:
Name: A descriptive name for the layer.
URL: URL template for the tile service (e.g., http://tile.stamen.com/watercolor/{z}/{x}/{y}.jpg).
Min. Zoom Level: Default is usually 0.
Max. Zoom Level: Set according to the tile service (e.g., 18).
Referer: Optional.
Tile Resolution: Leave as "Unknown" if not known.
Interpretation: Leave as "Default".
Save and Add the Layer:

Click Add to save and display the XYZ tile layer in your QGIS project.
Step 3: Configure QGIS2Web Plugin
Open QGIS2Web Plugin:

Go to Web > qgis2web > Create web map.
Configure Export Options:

Layers and Appearance: Select the layers to include in the web map.
Export Format: Choose between Leaflet or OpenLayers (Leaflet is commonly used).
Map Options: Set the extent, controls, and preview.
Step 4: Export the Web Map
Export Map:
Click Export.
Choose the directory to save the web map files.
The plugin will generate HTML, JavaScript, and CSS files.
Step 5: Access the Web Map
Local Preview:
Open the exported HTML file in a web browser to preview your web map locally.
Step 6: Customize the Map
Edit HTML/JavaScript/CSS:

For advanced customizations, manually edit the exported HTML, JavaScript, and CSS files.
Custom Scripts and Styles:

Custom Icon Function: Create custom icons for map markers.
Defining Colors and Places: Use JavaScript objects for node status and locations.
Sending Data to Backend: Define sendDataToBackend function to send data on marker click.
Periodic Data Update: Use setInterval to fetch updated data and update markers.
Adding Markers to the Map: Define addMarker function to add markers with popups.
Custom Leaflet Control: Extend Leaflet control for search functionality.
URL Parsing: Include method to extract location from URL and trigger geocode search.
Add Labels and Buttons:

Modify JavaScript code to add labels for victim locations and LoRa devices.
Configure labels to show a button that sends data to Grafana on click.
