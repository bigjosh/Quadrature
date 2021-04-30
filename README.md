# Arduino Hardware Quadrature Generator

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

## Example outputs

```
  // 250Hz, B about 5us behind behind A 
  startQuadrature( 250 , 1);
```
![DS1Z_QuickPrint5](https://user-images.githubusercontent.com/5520281/116673687-b485d380-a971-11eb-966f-1646fa4bcc32.png)

```  
  // 1KHz, A and B exactly in phase
  startQuadrature( 1000 , 0 );
```  
  ![DS1Z_QuickPrint4](https://user-images.githubusercontent.com/5520281/116673680-b0f24c80-a971-11eb-9b32-1c43ce39560b.png)

```
  // 10KHz, A and B exactly out of phase
  startQuadrature( 10000 , 180 );     //(-180 same result)
```  
  ![DS1Z_QuickPrint3](https://user-images.githubusercontent.com/5520281/116673643-a89a1180-a971-11eb-91c1-ea663456a4f6.png)

```
  // 100KHz, A leads B by 90 degrees
  startQuadrature( 100000 , 90 );
```  
![DS1Z_QuickPrint2](https://user-images.githubusercontent.com/5520281/116673633-a3d55d80-a971-11eb-9daa-632036aa5cf0.png)

```
  // 1MHz, B leads A by 90 degrees
  startQuadrature( 1000000 , -90 );
```  
![DS1Z_QuickPrint1](https://user-images.githubusercontent.com/5520281/116673601-961fd800-a971-11eb-9d1c-db16bc84c07a.png)
  
