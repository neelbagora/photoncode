// This #include statement was automatically added by the Particle IDE.
#include <SparkFun_Photon_Weather_Shield_Library.h>

// This #include statement was automatically added by the Particle IDE.
#include <SparkFun_Photon_Weather_Shield_Library.h>

#include "SparkFun_Photon_Weather_Shield_Library/SparkFun_Photon_Weather_Shield_Library.h"

Weather sensor;

float t = 0;    //actual temperature
float h = 0;    //humidity
float p = 0;    //pressure


void setup() {
    sensor.begin();
    sensor.setOversampleRate(7);
    sensor.setModeBarometer();
    delay(1000);
}

void loop() {
    getClimateData();
    publishData();
    delay(15000);
}

void getClimateData() {
    t = sensor.getTempF();
    h = sensor.getRH();
    p = sensor.readPressure();
}

void publishData() {
    char payload[255]; 

    //  {
    //      "t": ##.#
    //      "h": ##.#
    //      "p": ##.#
    //  }
    snprintf(payload, sizeof(payload), "{ \"t\": %.1f, \"h\": %.1f,  \"p\": %.1f}", 
    t, h, p * 0.001);
    Particle.publish("climate", payload, 60);
}

