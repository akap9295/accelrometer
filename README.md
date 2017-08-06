# accelrometer
package com.example.aksha.accelerometer;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.hardware.Sensor;
import android.hardware.SensorManager;
import android.hardware.SensorEvent;
import android.hardware.SensorEventListener;
import android.widget.TextView;

public class Main extends AppCompatActivity implements SensorEventListener {
    private TextView a,b,c;
    private Sensor ob1;
    private SensorManager ob2;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        ob2 = (SensorManager)getSystemService(SENSOR_SERVICE);
        ob1=ob2.getDefaultSensor(Sensor.TYPE_ACCELEROMETER);
        ob2.registerListener(this,ob1,SensorManager.SENSOR_DELAY_NORMAL);
        a=(TextView)findViewById(R.id.a);
        b=(TextView)findViewById(R.id.b);
        c=(TextView)findViewById(R.id.c);
    }
    @Override
    public void onAccuracyChanged(Sensor sensor, int accuracy) {
    }
    @Override
    public void onSensorChanged(SensorEvent event){
        a.setText("X: " + event.values[0]);
        b.setText("Y: " + event.values[1]);
        c.setText("Z: " + event.values[2]);
    }

}
