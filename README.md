# Quadrature
Arduino Quadrature Generator

Uses an Arduino UNo to generate quadrature output on pins 9 & 10.
Configurable freqnecy from ~122Hz to 4Mhz. (Lower freqencies possible) 
Confugrable phase shift from -180 deg to +180 deg. 

Main function:
```

// freq_hz is frequency in hertz from 122 to 4,000,000
// shift_deg is phase shift between output A and output B in degrees (values outside -180 to +180 are normalized)

// Note that at frequencies above 44KHz you will loose precision on phase shift. At 4Mhz, everything is rounded to just 0 or +/-90 degrees.
// Note that all timing happens in 1/16Mhz increments, so frequencies that do not land on integer multipules of that will be aproximiate. 
// Use startWaveforms() directly for more precise control. 

void startQuadrature( unsigned long freq_hz , int shift_deg  );
```
