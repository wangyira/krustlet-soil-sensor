# krustlet-soil-sensor
More information on [Krustlet: Kubernetes Kubelet in Rust for Running WASM](https://github.com/deislabs/krustlet)
## Hardwares used
- [Raspberry Pi 4 2GB](https://www.canakit.com/raspberry-pi-4-2gb.html)
- [Soil Moisture Sensor - pack of 5 includes jumper wires](https://www.amazon.com/gp/product/B071F4RDHY/ref=as_li_ss_tl?ie=UTF8&linkCode=sl1&tag=piddlerinther-20&linkId=77f1c0f9c67c51d76b687628afa62ce1&language=en_US) 
- [MCP 3008 ADC](https://www.amazon.com/Microchip-MCP3008-I-10-Bit-ADC-Pack/dp/B01HGCSGXM/ref=sr_1_2?dchild=1&keywords=mcp3008&qid=1597441622&sr=8-2)

## Raspberry Pi Set-up
### Wiring the Raspberry Pi
- See wiring.png for more details
- The first light on the soil sensor should lit up when plugged into power, the second light should lit up when submerged in water. 
- [Credit](https://maker.pro/raspberry-pi/tutorial/interfacing-soil-moisture-sensor-with-raspberry-pi)
### Enable the SPI interface on Raspberry Pi to read analog inputs from the sensor
- Launch the terminal and type `sudo raspi-config`
- Navigate to the interfacing options
- Enable the SPI interface
- Reboot the Raspberry Pi
- Install the spidev library 
```sudo apt-get install git python-dev
git clone git://github.com/doceme/py-spidev
cd py-spidev/
sudo python setup.py install
```

## Measuring Data
- Clone this repo and finish all the set-up above
- Run `python3 measure.py`
- The output ranges from 0 to 100. 0 being no resistance (air), 100 being high resistance (liquid).
- The sensor in air should display ~1, in dry soil should display 2-4, in wet soil should display 4-15, and in water should display 60-75. 
- The data from the soil sensor is written to data.txt
