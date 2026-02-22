# Wiring the Heater Relay

The RTM uses a relay to turn your heater on and off. If you have never used a relay before, think of it simply as an automatic switch. The RTM physically pushes the "switch" inside the relay to connect or disconnect the power going to your heater.

### ⚠️ DISCLAIMER & SAFETY WARNINGS ⚠️
**READ THIS BEFORE PROCEEDING.** * **Risk of Electric Shock or Fire:** Working with electricity, especially mains voltage (110V / 220V AC), is extremely dangerous. Incorrect wiring can result in catastrophic damage to your equipment, severe injury, or death.
* **Proceed at your own risk:** This guide is for informational purposes only. If you are not confident in your ability to safely wire electrical components, **STOP** and hire a qualified electrician. 
* **Always unplug everything:** Never attempt to wire, touch, or adjust the relay or heater while the power supply is plugged into the wall.
* **Use properly rated wire:** Ensure the wires you use are thick enough (proper AWG) to handle the amperage of your specific heater.

---

## How the Relay Works

On your relay module, you will see three terminals where you screw in your wires:
* **COM (Common):** This is where the main power *enters* the relay.
* **NO (Normally Open):** This is where power *exits* the relay to go to your heater. It is called "Normally Open" because the circuit is open (disconnected) by default. When the RTM calls for heat, it closes this connection, allowing electricity to flow.
* **NC (Normally Closed):** We **do not use** this terminal for this project.

> You only pass **ONE** wire through the relay (the "Live" or "Positive" wire). The relay simply cuts that wire in half and reconnects it when it's time to heat. The other wire (Neutral or Negative) goes straight from your power source to your heater. See the wiring diagram below.

### Wiring Diagram
![](images/relay_connection_diagram.png)

## Option A: Wiring a Low Voltage Heater (12V or 24V DC)

If your heater uses a DC power brick (like a laptop charger) or an LED power supply, follow these steps:



1. **Negative Wire (Black/Blue):** Connect the negative wire from your power supply directly to the negative terminal on your heater. It does not touch the relay.
2. **Positive Wire (Red/Brown) IN:** Run a wire from the positive terminal of your power supply into the **COM** port on the relay and tighten the screw.
3. **Positive Wire OUT:** Run a wire from the **NO** port on the relay to the positive terminal on your heater. 

---

## Option B: Wiring a Mains Voltage Heater (110V or 220V AC)

If your heater plugs directly into the wall outlet (like a PTC space heater, or fermentation belt), you will be cutting into an extension cord or appliance cable. **Double-check that the cord is unplugged from the wall!**

1. **Ground Wire (Green / Yellow & Green):** Connect the ground wire from your wall plug directly to the ground connection on your heater (if it has one). 
2. **Neutral Wire (White in US / Blue in EU):** Connect the neutral wire from your wall plug directly to the neutral connection on your heater. It does not touch the relay.
3. **Live/Hot Wire IN (Black in US / Brown in EU):** Connect the Live wire coming from your wall plug into the **COM** port on the relay.
4. **Live/Hot Wire OUT:** Run a wire from the **NO** port on the relay to the Live/Hot connection on your heater.

>(Safety Tip: Enclose your relay and all exposed AC wiring inside a plastic project box so no live contacts can be accidentally touched!)