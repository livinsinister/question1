In this code, we have:
1. Used the Python 'bleak' library which provides a cross-platform BLE API.
2. Instead of using the default battery level characteristic, our code defines a custom characteristic with a different UUID (00002A19-0000-1000-8000-00805F9B34FC). The 'flags' parameter in the 'BleakGATTCharacteristic' constructor is set to 0x0B to enable both read and notify operations.
3. The 'on_read' parameter is set to 'None' to indicate that the characteristic is read-only. This means that clients can read the current value of the characteristic, but they cannot write to it. The 'on_notify' parameter is set to the 'battery_level_handler' function, which is called when a client subscribes to notifications of the battery level characteristic.
4. The server advertises as "PC Battery" every 200ms and updates the battery level characteristic with the current battery percentage every second.
In order to test the BLE Peripheral using nRF connect app:
1. Using Bleak ≥ 0.13.0 
