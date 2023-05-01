In this code, we have:
1. Used the Python 'bleak' library which provides a cross-platform BLE API.
2. Instead of using the default battery level characteristic, our code defines a custom characteristic with a different UUID (00002A19-0000-1000-8000-00805F9B34FC). The    'flags' parameter in the 'BleakGATTCharacteristic' constructor is set to 0x0B to enable both read and notify operations.
3. The 'on_read' parameter is set to 'None' to indicate that the characteristic is read-only. This means that clients can read the current value of the characteristic,      but they cannot write to it. The 'on_notify' parameter is set to the 'battery_level_handler' function, which is called when a client subscribes to notifications of      the battery level characteristic.
4. The server advertises as "PC Battery" every 200ms and updates the battery level characteristic with the current battery percentage every second.

In order to test the BLE Peripheral using nRF connect app:
1. Go to the nRF connect app and go to the "GATT Configurator" tab. 
2. Click on the "Add Service" button to create a new service.
3. Enter a name for your service (e.g., "PC Battery"), and click "Create Service". Click on the "Add Characteristic" button to create a new characteristic.
   Enter a name for your characteristic (e.g., "Battery Level"), and set the UUID for the characteristic to a unique UUID that you've defined for your application.
4. Choose the "Read" & "Notify" property for the characteristic, since you want to be able to read the battery level from your peripheral. Set the value to "0*0A" in        order to enable both read and notify property. Click "Create Characteristic" to add the characteristic to your service.
5. Search the scan for nearby BLE Peripherals and locate your peripheral in the list of devices. You should see your peripheral's service name (e.g., "PC Battery")          listed in the list of services.
6. Click on your peripheral's name to connect to it. Once you're connected, go to the "Explorer" tab in the NRF Connect app and locate your peripheral's service and        characteristic in the list. Click on the characteristic to read its value. You should see the battery level of your PC displayed in the app.

