# WuKong IoT Final Project: SmartCans

#### 1. Equipment
* LCD text display x5
* trash cans x2
* ultrasonic distance detector x2
* catflap x2 (DIY with PE boards)
* LED light bulb x5
* Raspberry pi x5

#### 2. WuClasses
1. Assigner (master/ virtual)
    * keep track of all trash cans & garbage types
    * notify Alerter to change status
    * assets: types (*short*)
    * inputs: alert x5 (*boolean*, **Communicator**)
    * outputs: clean (*boolean*, **Alerter**), type x5 (*short*, **Communicator**)
2. Alerter (light actuator/ hard)
    * cleaning squad
    * inputs: clean (*boolean*)
    * outputs: none
3. Communicator (device/ virtual)
    * remember garbage type
    * control LCD displayer
    * communicate with assigner
    * inputs:  type (*short*, **Assigner**), is_full (*boolean*, **Communicator**) 
    * outputs: alert (*boolean*, **Assigner**), type (*short*, **Displayer**), lock (*boolean*, **Lock**)
4. Displayer (LCD displayer/ hard)
    * display garbage type
    * inputs: type (*short*, **Communicator**)
5. Lock (light actuator/ hard)
    * control lock according to *lock* from Communicator
    * inputs: lock (*boolean*, **Communicator**)
5. HeightTracker (ultrasonic detector/ hard)
    * track height inside trash can
    * outputs: is_full (*boolean*, **Communicator**)

* **Note**: type asset values and meanings
    * -1: trash can is unavailable
    * 0: general trash
    * 1: paper
    * 2: plastic

#### 3. Scenario & Operation
* Simulate 5 trash cans running on SmartCan application
* **Scenario**: 2-3 types of trash