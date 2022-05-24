# Python I2C Driver for Sensirion SHT4X

This repository contains the Python driver to communicate with the Sensirion
SHT4X sensor family over I2C. 

<center><img src="images/SHT4x.png" width="300px"></center>

Click [here](https://sensirion.com/products/catalog/SEK-SHT40/) to learn more about the Sensirion SHT4X sensor family.



## Supported sensor types

| Sensor name   | I²C Addresses  |
| ------------- | -------------- |
|[SHT40](https://sensirion.com/products/catalog/SHT40/)| **0x44**, 0x45|
|[SHT41](https://sensirion.com/products/catalog/SHT41/)| **0x44**, 0x45|
|[SHT45](https://sensirion.com/products/catalog/SHT45/)| **0x44**, 0x45|

The following instructions and examples use a *SHT40*.



## Usage

See user manual at
[https://sensirion.github.io](https://sensirion.github.io/python-i2c-sht4x).

#### Detaild sensor pinout

<img src="images/SHT40_pinout.png" width="300px">

| *Pin* | *Cable Color* | *Name* | *Description*  | *Comments* |
|-------|---------------|:------:|----------------|------------|
| 1 | green |SDA | I2C: Serial data input / output | 
| 2 | black |GND | Ground | 
| 3 | yellow |SCL | I2C: Serial clock input | 
| 4 | red |VDD | Supply Voltage | 1.1 to 3.6V
## Development

We develop and test this driver using our company internal tools (version
control, continuous integration, code review etc.) and automatically
synchronize the `master` branch with GitHub. But this doesn't mean that we
don't respond to issues or don't accept pull requests on GitHub. In fact,
you're very welcome to open issues or create pull requests :)

### Check coding style

The coding style can be checked with [`flake8`](http://flake8.pycqa.org/):

```bash
pip install -e .[test]  # Install requirements
flake8                  # Run style check
```

In addition, we check the formatting of files with
[`editorconfig-checker`](https://editorconfig-checker.github.io/):

```bash
pip install editorconfig-checker==2.0.3   # Install requirements
editorconfig-checker                      # Run check
```

### Run tests

Unit tests can be run with [`pytest`](https://pytest.org/):

```bash
pip install -e .[test]                       # Install requirements
pytest -m "not needs_device"                 # Run tests without hardware
pytest                                       # Run all tests
pytest -m "needs_device"                     # Run all tests for SHT4X

```

The tests with the marker `needs_device` have following requirements:

- The SHT4X sensor must be connected to a
  [SensorBridge](https://sensirion.com/products/catalog/SEK-SensorBridge/) on port 1.
- Pass the serial port where the SensorBridge is connected with
  `--serial-port`, e.g. `pytest --serial-port=COM7`
- The SensorBridge must have default settings (baudrate 460800, address 0)


### Build documentation

The documentation can be built with [Sphinx](http://www.sphinx-doc.org/):

```bash
python setup.py install                        # Install package
pip install -r docs/requirements.txt           # Install requirements
sphinx-versioning build docs docs/_build/html  # Build documentation
```

## License

See [LICENSE](LICENSE).
