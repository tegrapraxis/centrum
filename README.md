# Centrum

High-performance control systems platform with a C core and Python interface, designed for both rapid prototyping and production deployment. Centrum bridges the gap between development and industrial deployment with deterministic timing, safety features, and industrial protocol support.

[![C Version](https://img.shields.io/badge/C-C11-blue.svg)](https://en.wikipedia.org/wiki/C11_(C_standard_revision))
[![Python Version](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

## Architecture

- **C Core (libcentrum)**
  - Real-time control loops
  - Hardware abstraction layer
  - Industrial protocol implementations
  - Safety-critical components
  - Memory management
  - RTOS integration

- **Python Interface**
  - High-level configuration
  - System monitoring
  - Data analysis
  - Visualization
  - Rapid prototyping

## Core Features

### Industrial-Grade Control
```c
// C API for critical control loops
centrum_controller_t* ctrl = centrum_controller_create();
centrum_safety_limits_t limits = {
    .max_velocity = 3000.0,    // RPM
    .max_current = 10.0,       // Amps
    .position_limits = {-180.0, 180.0}
};
centrum_controller_set_safety(ctrl, &limits);
```

### Python Interface for Configuration
```python
from centrum import Controller, SafetyLimits

controller = Controller()
controller.set_safety_limits(
    max_velocity=3000,  # RPM
    max_current=10,     # Amps
    position_limits=(-180, 180)
)
```

### Industrial Protocol Support
- EtherCAT
- Profinet
- Modbus TCP/RTU
- OPC UA
- CAN/CANopen
- EtherNet/IP

### Safety Features
- Emergency stop systems
- Watchdog timers
- Redundant sensors
- Fault detection
- Error recovery
- Safety limit enforcement
- System state validation

### Production Monitoring
- Real-time performance metrics
- System health monitoring
- Predictive maintenance
- Quality metrics
- OEE calculations
- SCADA integration

## Use Cases

### Manufacturing
- CNC machine control
- Robot cell coordination
- Process automation
- Quality control systems

### Motion Control
- Multi-axis coordination
- Servo control
- Precision positioning
- Synchronization

### Process Control
- Temperature regulation
- Flow control
- Pressure management
- Chemical processes

## Performance

- < 1μs control loop jitter
- Deterministic timing
- Real-time scheduling
- Memory-efficient design
- Zero-copy data handling
- DMA utilization

## Installation

### C Library
```bash
git clone https://github.com/centrum/centrum.git
cd centrum
mkdir build && cd build
cmake ..
make
sudo make install
```

### Python Package
```bash
pip install centrum
```

## Quick Start

### C Implementation
```c
#include <centrum.h>

int main() {
    centrum_config_t config = {
        .sampling_rate = 1000,  // Hz
        .priority = CENTRUM_PRIORITY_REALTIME
    };
    
    centrum_controller_t* ctrl = centrum_controller_create(&config);
    centrum_controller_start(ctrl);
    
    // Control loop runs in separate real-time thread
    while(centrum_controller_is_running(ctrl)) {
        centrum_process_events(ctrl);
        centrum_update_monitoring(ctrl);
    }
    
    centrum_controller_destroy(ctrl);
    return 0;
}
```

### Python Usage
```python
from centrum import Controller

controller = Controller(sampling_rate=1000)  # Hz
controller.configure_industrial_interface(
    protocol="EtherCAT",
    device_id=1,
    cycle_time_us=1000
)

# Start control system
controller.start()

# Monitor in real-time
for status in controller.monitor():
    print(f"Position: {status.position}, Error: {status.error}")
```

## Documentation
- [C API Reference](https://centrum.dev/c-api)
- [Python API Guide](https://centrum.dev/python-api)
- [Industrial Integration](https://centrum.dev/industrial)
- [Safety Guidelines](https://centrum.dev/safety)
- [Performance Tuning](https://centrum.dev/performance)

## Building from Source

### Requirements
- C11 compatible compiler
- CMake 3.15+
- Python 3.8+ (for Python interface)
- Industrial protocol SDKs (optional)

### Build Options
```bash
# Full build with all features
cmake -DCENTRUM_BUILD_ALL=ON ..

# Minimal real-time core
cmake -DCENTRUM_MINIMAL=ON ..

# With specific industrial protocols
cmake -DCENTRUM_ETHERCAT=ON -DCENTRUM_PROFINET=ON ..
```

## License
This project is licensed under the MIT License - see [LICENSE](LICENSE) for details.

## Contributing
See [CONTRIBUTING.md](CONTRIBUTING.md) for development setup and guidelines.

## Commercial Support
- Implementation consulting
- Custom protocol integration
- Safety certification support
- Training and workshops
- Production deployment assistance
