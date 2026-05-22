# Proyecto simulador de circuitos

## kdjsjsnzsn:

## Introducción:

## Objetivos:

### *Objetivo general:*

### *Objetivos específicos:*


## Lógica del programa:

## Diagrama de flujo:

```
mermaid

classDiagram
    class Component {
        <<abstract>>
        +str name
        +float voltage
        +float current
        +reset()* 
    }
    class VoltageSource {
        +float source_voltage
        +set_voltage(voltage)
        +reset()
    }
    class Switch {
        +float t_close
        -bool _closed
        +is_closed(t) bool
        +set_t_close(t_close)
        +reset()
    }
    class Resistor {
        +float resistance
        +set_resistance(resistance)
        +reset()
    }
    class Capacitor {
        +float capacitance
        +float initial_voltage
        +set_capacitance(capacitance)
        +set_initial_voltage(v0)
        +reset()
    }
    class Inductor {
        +float inductance
        +float initial_current
        +set_inductance(inductance)
        +set_initial_current(i0)
        +reset()
    }
    Component <|-- VoltageSource
    Component <|-- Switch
    Component <|-- Resistor
    Component <|-- Capacitor
    Component <|-- Inductor

    class BaseCircuit {
        <<abstract>>
        +VoltageSource source
        +Switch switch
        +float t_end
        +float dt
        +ndarray time
        -dict _results
        +run()
        +plot(output_dir, show) list
        +set_time(t_end, dt)
        #_get_passive_components()* list
        #_derivatives(t, state, vs)* ndarray
        #_state_to_component_values(t, state, vs)*
        #_initial_state()* ndarray
        #topology_name()* str
        -_component_param_str(comp)$ str
    }
    class RCSeries {
        +Resistor resistor
        +Capacitor capacitor
        +topology_name() str
        #_initial_state() ndarray
        #_derivatives(t, state, vs) ndarray
        #_state_to_component_values(t, state, vs)
        #_get_passive_components() list
    }
    class RCParallel {
        +Resistor resistor
        +Capacitor capacitor
        -float _RS
        +topology_name() str
        #_initial_state() ndarray
        #_derivatives(t, state, vs) ndarray
        #_state_to_component_values(t, state, vs)
        #_get_passive_components() list
    }
    class RLSeries {
        +Resistor resistor
        +Inductor inductor
        +topology_name() str
        #_initial_state() ndarray
        #_derivatives(t, state, vs) ndarray
        #_state_to_component_values(t, state, vs)
        #_get_passive_components() list
    }
    class RLParallel {
        +Resistor resistor
        +Inductor inductor
        -float _RS
        +topology_name() str
        #_initial_state() ndarray
        #_derivatives(t, state, vs) ndarray
        #_state_to_component_values(t, state, vs)
        #_get_passive_components() list
    }
    class RLCSeries {
        +Resistor resistor
        +Inductor inductor
        +Capacitor capacitor
        +topology_name() str
        #_initial_state() ndarray
        #_derivatives(t, state, vs) ndarray
        #_state_to_component_values(t, state, vs)
        #_get_passive_components() list
    }
    class RLCParallel {
        +Resistor resistor
        +Capacitor capacitor
        +Inductor inductor
        -float _RS
        +topology_name() str
        #_initial_state() ndarray
        #_derivatives(t, state, vs) ndarray
        #_state_to_component_values(t, state, vs)
        #_get_passive_components() list
    }
    BaseCircuit <|-- RCSeries
    BaseCircuit <|-- RCParallel
    BaseCircuit <|-- RLSeries
    BaseCircuit <|-- RLParallel
    BaseCircuit <|-- RLCSeries
    BaseCircuit <|-- RLCParallel
    BaseCircuit o-- VoltageSource : source
    BaseCircuit o-- Switch : switch
    RCSeries o-- Resistor
    RCSeries o-- Capacitor
    RCParallel o-- Resistor
    RCParallel o-- Capacitor
    RLSeries o-- Resistor
    RLSeries o-- Inductor
    RLParallel o-- Resistor
    RLParallel o-- Inductor
    RLCSeries o-- Resistor
    RLCSeries o-- Inductor
    RLCSeries o-- Capacitor
    RLCParallel o-- Resistor
    RLCParallel o-- Capacitor
    RLCParallel o-- Inductor
```

## Interfaz gráfica: