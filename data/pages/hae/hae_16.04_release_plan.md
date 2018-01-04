# CDM Service Framework 16.04 Release Plan

## Introduction


*  Dev Lead : Inhwan Choi

*  QA Lead  : Stefano Toppan

## Themes and Priorities

The 16.04 release of the Common Device Model (CDM) service framework is the first official release of the CDM service framework project. It is designed to be compatible with AllJoyn Core and Base Services 16.04. The following features will be available:


*  CDM service framework that supports both SCL and TCL

*  Samples
    * Device Emulator
    * Integrated Controllee/Controller
    * Android Integrated Controller

*  UnitTests : test set for each CDM interfaces

*  Developer Documentation

*  CDM interfaces as following:

 | Namespace   | Interfaces                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 
 | ---------   | ----------                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 
 | environment | CurrentAirQuality, CurrentAirQualityLevel, CurrentHumidity, CurrentTemperature, TargetHumidity, TargetTemperature, TargetTemperatureLevel, WaterLevel, WindDirection                                                                                                                                                                                                                                                                                                                          | 
 | operation   | AirRecirculationMode, Alerts, AudioVideoInput, AudioVolume, BatteryStatus, Channel, ClimateControlMode, ClosedStatus, CurrentPower, CycleControl, DishWashingCyclePhase, EnergyUsage, FanSpeedLevel, FilterStatus, HeatingZone, HvacFanMode, LaundryCyclePhase, MoistureOutputLevel, OffControl, OnControl, OnOffStatus, OvenCyclePhase, PlugInUnits, RapidMode, RapidModeTimed, RemoteControllability, RepeatMode, ResourceSaving, RobotCleaningCyclePhase, SoilLevel, SpinSpeedLevel, Timer | 
 | input       | Hid                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | 

The following are components that were incomplete or were not in the unofficial 16.04 release (new work to be done):

*  CDM interfaces as following:

 | Namespace             | Interfaces                                       | 
 | ---------             | ----------                                       | 
 | UserInterfaceSettings | LanguageDisplay, TemperatureDisplay, TimeDisplay | 

## Deliverables

Common Device MOdel (HAE) Service Framework Project

## Milestones

 | Milestone                                | Date          | Details | 
 | ---------                                | ----          | ------- | 
 | Draft AllJoyn Interface Definitions      | Jul. 24, 2015 | Done    | 
 | IRB Approval of Interface Definitions    | Oct. 16, 2015 | Done    | 
 | High-level design (HLD) document         | Nov. 13, 2015 | Done    | 
 | IRB Reaffirmed the updates to Interfaces | Aug. 20, 2016 | Done    | 
 | Code Freeze                              | Aug. 24, 2016 | Done    | 
 | QA Complete                              | Sep.  2, 2016 | Done    | 



## Expected Work Group Dependencies


*  Core 16.04

*  Base Services 16.04

## Compatibility with Previous Releases

N/A
