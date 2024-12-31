# Centrum

A powerful Python-based control systems development platform that bridges theory and implementation. Centrum provides a flexible, extensible framework for rapid prototyping and deployment of control applications, from simple motor control to complex robotic systems.

[![Python Version](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

## 🎯 Core Features

- **Real-time Control Loop Implementation**
  - Configurable sampling rates
  - Multi-threading support for parallel control loops
  - Precise timing control
  
- **Hardware Interfaces**
  - Motor driver support (DC, Stepper, BLDC)
  - Position/velocity sensor integration
  - Temperature sensor interfaces
  - Extensible driver architecture

- **Control Algorithms**
  - PID control with anti-windup
  - State feedback controllers
  - Feed-forward compensation
  - Custom controller support

- **Data Handling**
  - Real-time data logging
  - Performance metrics
  - System identification tools

## 🚀 Common Applications

- Motor position and velocity control
- Robotic arm manipulation
- Balance systems (inverted pendulum)
- Temperature control systems
- Process automation
- Educational demonstrations

## 🛠️ Installation

```bash
pip install centrum
```

## 📖 Quick Start

```python
from centrum.core import PIDController
from centrum.drivers import DCMotor, Encoder

# Initialize hardware
motor = DCMotor("motor1", pwm_pin=18, dir_pin=23)
encoder = Encoder("encoder1", pin_a=24, pin_b=25)

# Configure controller
controller = PIDController(
    sensor=encoder,
    actuator=motor,
    kp=1.0, ki=0.1, kd=0.05,
    sampling_time=0.01  # 10ms
)

# Run control loop
controller.set_target(90.0)  # degrees
status = controller.step()
```

## 📊 Example: Motor Position Control

```python
import time
from centrum.examples import PositionControl

# Create position control system
system = PositionControl(
    motor_pins={'pwm': 18, 'dir': 23},
    encoder_pins={'a': 24, 'b': 25}
)

# Configure and run
system.set_position(180)  # degrees
system.run(duration=5.0)  # seconds
```

## 🔧 Requirements

- Python 3.8+
- NumPy
- RPi.GPIO (for Raspberry Pi implementations)
- Additional optional dependencies based on usage

## 📈 Roadmap

- [ ] Advanced control algorithms (MPC, LQR)
- [ ] Web-based monitoring interface
- [ ] Extended hardware support
- [ ] Real-time visualization tools
- [ ] System identification module
- [ ] Simulation environment

## 🤝 Contributing

Contributions are welcome! See our [Contributing Guidelines](CONTRIBUTING.md) for details on:
- Setting up development environment
- Code style guidelines
- Submission process
- Bug reports and feature requests

## 📜 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) for details.

## ✨ Project Structure

```
centrum/
├── core/                 # Core control system implementations
├── drivers/              # Hardware interface drivers
├── algorithms/           # Control algorithms
├── utils/               # Utility functions and tools
├── examples/            # Example implementations
└── tests/               # Test suite
```

## 📫 Contact & Support

- GitHub Issues: Bug reports and feature requests
- Discord: [Join our community](https://discord.gg/centrum)
- Documentation: [Read the Docs](https://centrum.readthedocs.io/)

## 🙏 Acknowledgments

Built with support from the open-source community and control systems enthusiasts worldwide.
