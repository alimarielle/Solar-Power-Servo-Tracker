# --- Reset Function ---
def on_button_pressed_a():
    global power
    # Move servo back to start position (0 degrees)
    fwdMotors.set_angle(fwdBase.left_servo, 0)
    # Clear the power variable
    power = 0

input.on_button_pressed(Button.A, on_button_pressed_a)

# --- Power Calculation ---
def calculatePower():
    global current_Amps, power
    # Read current in milliamps and convert to Amps (I)
    current_Amps = fwdSensors.current1.current() / 1000
    # Calculate Power (P = I * V) using voltage sensor data
    power = current_Amps * fwdSensors.voltage1.voltage()

# --- Initial Setup ---
power = 0
current_Amps = 0
# Move servo to starting position at boot
fwdMotors.set_angle(fwdBase.left_servo, 0)

# --- Main Logic Loop ---
def on_forever():
    calculatePower()
    
    # Check if we have found a significant power source (> 0.3 Watts)
    if power > 0.3:
        # Display the power level as a bar graph on the LEDs
        led.plot_bar_graph(power, 1000)
    else:
        # If power is low, keep searching:
        basic.show_icon(IconNames.SMALL_DIAMOND)
        
        # Increment servo angle by 10 degrees to "seek" better light/power
        fwdMotors.set_angle(fwdBase.left_servo,
            fwdMotors.get_angle(fwdBase.left_servo) + 10)
        
        # If we reach the end of the rotation (180 deg), reset to 0
        if fwdMotors.get_angle(fwdBase.left_servo) > 180:
            fwdMotors.set_angle(fwdBase.left_servo, 0)

basic.forever(on_forever)
