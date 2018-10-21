# Balloon_Calculator

A macro-enabled Excel balloon calculator:
- Calculates the burst altitude or ascent rate for single or dual balloon launches with Helium or Hydrogen fill
- Also calculates the expected float altitude for a single balloon launch
- Supports Kaymont Totex, Hwoyee and Pawan balloons
- Based extensively on the [CUSF Burst Calc](https://github.com/ukhas/cusf-burst-calc)
- With thanks to Steve Randall, Adam Grieg et al

Uses macros to calculate the atmospheric temperature, pressure and density plus the burst altitude.
You may need to Enable Macros before the calculator will work correctly.

## Single_Balloon__Burst_Altitude

This sheet calculates the neck lift, ascent rate and time to burst for the chosen balloon based on the desired burst altitude:

- Use the pull-down menu in cell C6 to select the balloon type.
- Enter the actual coefficient of drag in cell C9. If you don't have an accurate coefficient based on previous flight data, copy the manufacturer's value from cell C8.
- Enter the weight of your balloon fill kit in cell C10. If you aren't using a fill kit, just enter zero.
- Enter the weight of your payload in cell C12.
- Use the pull-down menu in cell C13 to select the gas type.
- Enter the altitude of your launch site (metres above sea level) in cell C14.
- Enter the actual atmospheric temperature in cell C16. If you don't have an accurate reading, copy the model temperature from cell C15.
- Enter the actual balloon gas temperature in cell C17. Again, use the model temperature if you don't have an accurate figure. Remember that the balloon gas will be a little colder than the atmosphere unless the balloon has been left to stabilise.
- Enter the actual atmospheric pressure in cell C19. If you don't have an accurate reading, copy the model pressure from cell C18.
- Cell C22 defines the balloon membrane pressure at launch (the difference between the balloon gas pressure and atmospheric pressure caused by the elasticity of the balloon). Leave this set to 0.15 kPa unless you have a more accurate figure.
- Cell C23 defines the balloon membrane pressure at burst. Leave this set to zero unless you have a more accurate figure.
- Enter the desired burst altitude in cell C26.

The spreadsheet will calculate the volume of the balloon at burst, how many mols of gas the balloon contains and then:

- The required volume of gas in cell C34.
- The required balloon neck lift (in kg) in cell C38.
- The approximate ascent rate in cell C40.
- The approximate time to burst in cell C41.

## Single_Balloon__Ascent_Rate

This sheet calculates the neck lift, burst altitude and time to burst for the chosen balloon based on the desired ascent rate:

- Use the pull-down menu in cell C6 to select the balloon type.
- Enter the actual coefficient of drag in cell C9. If you don't have an accurate coefficient based on previous flight data, copy the manufacturer's value from cell C8.
- Enter the weight of your balloon fill kit in cell C10. If you aren't using a fill kit, just enter zero.
- Enter the weight of your payload in cell C12.
- Use the pull-down menu in cell C13 to select the gas type.
- Enter the altitude of your launch site (metres above sea level) in cell C14.
- Enter the actual atmospheric temperature in cell C16. If you don't have an accurate reading, copy the model temperature from cell C15.
- Enter the actual balloon gas temperature in cell C17. Again, use the model temperature if you don't have an accurate figure. Remember that the balloon gas will be a little colder than the atmosphere unless the balloon has been left to stabilise.
- Enter the actual atmospheric pressure in cell C19. If you don't have an accurate reading, copy the model pressure from cell C18.
- Cell C22 defines the balloon membrane pressure at launch (the difference between the balloon gas pressure and atmospheric pressure caused by the elasticity of the balloon). Leave this set to 0.15 kPa unless you have a more accurate figure.
- Cell C23 defines the balloon membrane pressure at burst. Leave this set to zero unless you have a more accurate figure.
- Enter the desired ascent rate in cell C26.

The spreadsheet uses Cardano's method to solve the drag equation and calculate the balloon diameter at launch. It will then calculate:

- The required balloon neck lift (in kg) in cell C39.
- The required volume of gas in cell C41.
- The burst altitude in cell C45.
- The approximate time to burst in cell C49.

The altitude at which the balloon would float, if it does not burst first, is calculated in cell C50.
Cell C51 indicates whether the balloon will float or burst. The balloon volume at float, as a percentage of the burst volume, is calculated in cell C55.
This indicates how close the balloon will be to bursting at float.

## Single_Balloon__Floater

This sheet calculates the expected float altitude for the flight, based on the free lift (at launch).

- Use the pull-down menu in cell C6 to select the balloon type.
- Enter the actual coefficient of drag in cell C9. If you don't have an accurate coefficient based on previous flight data, copy the manufacturer's value from cell C8.
- Enter the weight of your balloon fill kit in cell C10. If you aren't using a fill kit, just enter zero.
- Enter the total weight of your payload in cell C12, including the weight of the cord or line.
- Use the pull-down menu in cell C13 to select the gas type.
- Enter the altitude of your launch site (metres above sea level) in cell C14.
- Enter the actual atmospheric temperature in cell C16. If you don't have an accurate reading, copy the model temperature from cell C15.
- Enter the actual balloon gas temperature in cell C17. Again, use the model temperature if you don't have an accurate figure. Remember that the balloon gas will be a little colder than the atmosphere unless the balloon has been left to stabilise.
- Enter the actual atmospheric pressure in cell C19. If you don't have an accurate reading, copy the model pressure from cell C18.
- Cell C22 defines the balloon membrane pressure at launch (the difference between the balloon gas pressure and atmospheric pressure caused by the elasticity of the balloon). Leave this set to 0.15 kPa unless you have a more accurate figure.
- Cell C33 defines the balloon membrane pressure at float. Leave this set to 0.15 kPa unless you have a more accurate figure.
- Enter the free lift in cell C25. This is the lift as measured _below_ the payload. The corresponding balloon neck lift is calculated in cell C27.

The spreadsheet will calculate:

- The balloon volume at launch in cell C28.
- The required volume of gas in cell C29.
- The mols of lift gas in cell C32.
- The expected float altitude in cell C36.
- The balloon volume at float, as a percentage of the burst volume, in cell C40.
- The approximate ascent rate in cell C42.
- The approximate time to float in cell C43.

The fill colour of cell C40 will change to: pink above 75%; red above 100%.

By adjusting the free lift in C25, you can calculate the best compromise for your flight based on the desired float altitude, ascent rate and % balloon fill at float.
The temperature at the float altitude may be important for your flight too, depending on how robust your electronics are.

## Dual_Balloon__Ascent_Rate

This sheet calculates neck lifts, required gas volumes and time to separation for a dual balloon launch.

Enter the data for the chosen balloons, payload and launch conditions as you did for the single balloon. Then:
- Enter the separation altitude in cell C35.
- Enter the desired ascent rate in cell C36.

The spreadsheet calculates the volume of gas and required neck lift of the float balloon, by assuming that the balloon will provide zero lift at separation. I.e. your flight should float at the separation altitude until you cut it down.
It will then calculate the volume of gas and required neck lift for the lift balloon by again using Cardano's method to solve the drag equation.

## Dual_Balloon__Neck_Lift

This sheet will calculate the ascent rate of the flight after separation, based on the neck lifts of both lift and float balloons.

It is useful to copy across the calculated values from the Dual_Balloon__Ascent_Rate sheet into this sheet and then:
- Adjust the float balloon neck lift in cell C14 up or down to provide the ascent rate of your flight after separation.
- Keep checking cell C69 while you adjust the float balloon neck lift until you see your desired ascent rate. You can opt for the flight to slowly descend after separation, instead of continuing to ascend. Cell C68 will show DOWN or UP accordingly.
- Now adjust the neck lift of the lift balloon in cell C21 until you see your desired ascent rate in cell C52.
- The time to separation is shown in cell C54.

Using this sheet, it is possible to define an ascent rate of 5 m/s to separation and then for the flight to continue upwards at (e.g.) 1 m/s until burst or cut-down.

### Licence

This project is distributed under an [MIT License](https://github.com/PaulZC/Balloon_Calculator/blob/master/LICENSE)

Enjoy!

**_Paul_**











