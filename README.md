# Cycloidal-Gearbox
Documentation of the engineering design process of building a cycloidal drive. From idea, constraints, CAD, prototyping, and manufacturing the final product

<img width="380" height="480" alt="image" src="https://github.com/user-attachments/assets/1ba97db5-52bb-4194-b9f1-2a1b376d9581" />
<img width="600" height="480" alt="image" src="https://github.com/user-attachments/assets/40efd266-714b-4790-a340-cea5ace527e0" />


## Design Requirements
The cycloidal drive project started as a project for my research lab (CoRE) where I am working to build a medical apparatus to experiment with human propioception. The device needed a strong motor/gearbox capable of producing enough torque to life a human leg from the sitting position, as well as the standing position.

Constraints included:
  - High torque capable of liting a human leg
  - Quiet gear box
  - Compact design
  - Minimal backlash
  - Durable

This led to the cycloidal drive design, which sastisfied these constrains and after discussions with my PI, gained approval for me to start researching and developing the drive.

## Design Process

### Cycloid Profile Generation
The cycloidal disk geometry was generated using standard cycloidal equations referenced from this SOLIDWORKS article [Building-a-Cycloidal-Drive](https://blog-assets.solidworks.com/uploads/sites/3/Building-a-Cycloidal-Drive-with-SOLIDWORKS.pdf).

The 4 main parameters were:

- Roller count (N) = 17
- Roller radius (Rr) = 6mm
- Rotor radius (R) = 50mm
- Eccentricity (E) = 1.8mm

With assistance from Claude, multiple geometries were evaluated to balance:
- Torque capacity
- Manufacturability
- Smooth operation

<img width="620" height="400" alt="Cycloidal gear profile generation 133200" src="https://github.com/user-attachments/assets/094ee28b-df56-4810-9c0d-832efebd0446" />
<img width="600" height="450" alt="image" src="https://github.com/user-attachments/assets/5f837f99-8267-4a47-ad5a-8d1fd0fe1dbb" />


Based on the profile of the drive set by these parameters, they would define the rest of the assembly: housing, eccentric shaft, and output disk.

Note: This cycloidal drive design will utilize 2 cycloidal gears off set 180 from each other to balance out eccentric forces. Hence the need for an indicator of somekind 

### Housing
The housing would encase the entire assembly and roller pins for the gear profiles to engage with.

The roller pins with have a radius of 6mm and sit on a construction circle equal to the rotor radius of 50mm. These were the 2 critical dimensions for the housing and the rest of the design focused on fully encasing the assembly along with screw and threaded insert holes.

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/a6860f05-8221-42c0-8501-2cd891340e3e" />

### Eccentric Shaft
The eccentric shaft's function is to engage the cycloidal profile with the roller pins. Creating the gear reduction and inverse rotation for the output pins.

The critical dimesions of the shaft is the eccentricity made by offsetting the center of the journal profile by 1.8mm. For this cycloidal drive design, the 2 cycloidal gears will sit 180 degrees offsetted from each other to cancel out the eccentric forces and reduce vibrations.

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/ecf909bf-f812-47a1-b754-a05e1880b54b" />

The red marks show the 1.8mm offset and in the center, both eccentric sections are offsetted by a total of 3.6mm. The shaft was designed to be printed in 3 seperate sections and joined together with 2 M4 screws traveling through the entire shaft. Shaft features raised borders to seperate each section and the shaft diameter was toleranced to be 19.9mm, which gives a snug fit of 0.1mm with the bearing.

### Output Disk
The output disk consists 2 sections joined together by screws and bearings to form the gear assembly. The output disk house the output pins whihc slots through output holes of the cycloid gear and transmit the gear's internal rotation into output torque. The first section is the base, where the input side sits and the second section is the cap where the output is transmitted.

The critical dimensions consist of the output pin diameter and the output pin construction circle, which can be set independently to the 4 main paramenters.

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/2aeb2fd3-98e2-4df6-a02b-cfedceaf595e" />
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/2594dfdb-cd94-42a3-af91-507f3bf49989" />
<img width="360" height="480" alt="image" src="https://github.com/user-attachments/assets/e5f0f208-5af8-490d-9924-86123eb0bf7e" />



Both disks features a compliance cut around the center hole to give way to tight tolerances, reducing contact points and introducing flex to the contact, allowing for more forgiving fits of the output bearings. Additionally, threaded insert holes are modelled in for secure screw connections and repeatability.

## Key Engineering Challenges

### Bearing Fit
Initial prototypes produced undersized bearing bores due to PETG dimensional inaccuracies.

Solutions:
- Adjusted hole clearances
- Added compliance slots
- Tuned slicer XY compensation
- Performed iterative print testing

### Output Pins
Several output pin clearances were evaluated to reduce binding while minimizing backlash.

The final design calculated the output pin holes to be the (diameter + 2*eccentricity) to provide minimal backlass. Testing showed that approximately 0.2 mm radial clearance provided reliable operation. 

## Manufacturing

### Processes

- FDM 3D Printing with:
  - Prusa i3 MK3s+
  - PETg filament
 
### BOM
| Item                                                      | Note                                                  | Quantity | Price  | Total      | Link         |
| --------------------------------------------------------- | ----------------------------------------------------- | -------- | ------ | ---------- | ------------ |
| PETG Filament                                             | Stronger and more secure structure                    | 2        | $0.00  | $0.00      | Already have |
| Shaft Bearings (20mm ID × 32mm OD × 10mm W, 10-pack)      | For cycloid rotors and output disk (4)                | 1        | $12.29 | $12.29     | [Link](https://www.amazon.com/uxcell-6804ZZ-Groove-Bearings-Shielded/dp/B082PWB7R5/ref=sr_1_6?crid=1474W0V9PI41U&dib=eyJ2IjoiMSJ9.X3hdz7otYEXoKpIs1g6kiBlNaXdqJqYREsxohsS8FM3cDOZdyeq5KnRIIaNFu1nZ-3zZOQ1xEdufQTxf8nyLcwh0koF1d7R8EExUdiNL355Y7aj-JZOCed5qFSYwZNrtg2LrQ8k5wbmbIKIVSriUE6c6HqQi4yjOfdBUiqgcycyuo4rMDESHUNOKlJf5ZB2HAxmOIG6mubKcypkHI6spLtTFD2FAfawceYph6Xwd4vo.M1RLKB5iNAiekMtfPwWsaUIO9qEie00P_QV5FhOJrH4&dib_tag=se&keywords=32mm%2Bouter%2Bdiameter%2Bball%2Bbearing&qid=1778819927&sprefix=32mm%2Bouter%2Bdiameter%2Bball%2Bbearing%2Caps%2C147&sr=8-6&th=1)         |
| Roller Bearings (4mm ID × 12mm OD × 4mm W, 20-pack)       | For rollers (34) and output disk pins (12), 46 total  | 3        | $9.99  | $29.97     | [Link](https://www.amazon.com/uxcell-6804ZZ-Groove-Bearings-Shielded/dp/B082PWB7R5/ref=sr_1_6?crid=1474W0V9PI41U&dib=eyJ2IjoiMSJ9.X3hdz7otYEXoKpIs1g6kiBlNaXdqJqYREsxohsS8FM3cDOZdyeq5KnRIIaNFu1nZ-3zZOQ1xEdufQTxf8nyLcwh0koF1d7R8EExUdiNL355Y7aj-JZOCed5qFSYwZNrtg2LrQ8k5wbmbIKIVSriUE6c6HqQi4yjOfdBUiqgcycyuo4rMDESHUNOKlJf5ZB2HAxmOIG6mubKcypkHI6spLtTFD2FAfawceYph6Xwd4vo.M1RLKB5iNAiekMtfPwWsaUIO9qEie00P_QV5FhOJrH4&dib_tag=se&keywords=32mm%2Bouter%2Bdiameter%2Bball%2Bbearing&qid=1778819927&sprefix=32mm%2Bouter%2Bdiameter%2Bball%2Bbearing%2Caps%2C147&sr=8-6&th=1)         |
| Output Disk Bearings (35mm ID × 62mm OD × 14mm W, 2-pack) | For output disk to housing (2)                        | 1        | $9.99  | $9.99      | [Link](https://www.amazon.com/HiPicco-6007-2RS-Bearings-Bearing-Pre-Lubricated/dp/B0CH2WVW4V/ref=sr_1_5?crid=173R35KP253R6&dib=eyJ2IjoiMSJ9.HtFZOxRd8AzK5EUTWw9iTwsRtxMy5tmNX2iwQyQiDgQAl3dLxo2klZTW1qFlr4Rzht5VbAgiEOIQp5kuqYZARtvD0-mXBilLcbD80wQ-FNrvqAvhUEGvUAhX24b8q5A8C2rklv1msNZJRHiouQeKFnCVmkU9V6lNudwnQvrUE0X5IU_MuAae4u55WFvLR4rNkBNucdFoWEoqD0hSUHsjh9FlS-Gqg-rv_31xRd1b-3U.X2XWl8u2lFNGo2LNoTCqvOWb7Atsp4L_XR3toJp-880&dib_tag=se&keywords=35mm%2Bid%2Bbearing&qid=1778824542&sprefix=3mm%2Bid%2Bbearing%2Caps%2C171&sr=8-5&th=1)         |
| M4 × 40mm Phillips Head Screws (15-pack)                  | For output disk pins (6)                              | 1        | $5.97  | $5.97      | [Link](https://www.amazon.com/Machine-Stainless-Assortment-Phillips-Furniture/dp/B0DLGT59V3/ref=sr_1_4?crid=2MMQ3GG67AM0D&dib=eyJ2IjoiMSJ9.PQC-fyMV8pTdu_NeBqQcDaJ01_uc0Ey6i3KLxz1dFEhH0idw-Gm8eLaA7z4-DsoEEbcwWeFw8z36WPxTWhmn5MllPNrz8jdTMqw-BmExY8VV2cutaQwVSg7cqFQSJLPI9W45zWFshdN0B-5ZF-dERtI-gJbWYcTIqjLqhF-6RjhgzPgFb6CZngOtWa1FJmv3Oy5H4mnxNblVaQ3SwNHrto_U3iXRdUo6CCXPYRypTW4.i3RkIEvL02NekkACqqNKoIZgSEZVIX7L25kx0zR-yDI&dib_tag=se&keywords=4mm%2Bx%2B40%2Bmm%2Bscrews&qid=1779261444&sprefix=4mm%2Bx%2B40%2Bmm%2Bscrews%2Caps%2C173&sr=8-4&th=1)         |
| M4 × 65mm Hex Screws (10-pack)                            | For eccentric shaft (2) and housing cap (8), 10 total | 1        | $5.00  | $5.00      | [Link](https://www.amazon.com/Stainless-Machine-Hexagon-Fastener-Quantity/dp/B0CG1NMPCT/ref=sr_1_11?crid=11KXA4TQIBO17&dib=eyJ2IjoiMSJ9.QDGudxVcjiNj-7q9BTprV_pYPBsjHy-ZFy0KIcxQjD81OSyV6ZZDuHR9ZWD_Q-K_56_t6pqlrVHJLUvAWrGSyyZs7gf-si0EjjvvXyioQ7LfVFHvm9xEykC6wuWrHepBKAyAFfbKz6CXsNGNlb3HrURBZYlq2IVKkhC4XLcHZwhWm_rKEoNsu-DCnZOU8Cbqyt7obZTOD29TkUpVyXKKbiHL0qEl1XSBHqhGXaz34w8.iczIjMds6PLeUsjlItWHJGD8hq6O_eDhNMDDYZ_Vfyg&dib_tag=se&keywords=m4%2Bx%2B65mm%2Bscrew&qid=1779209425&sprefix=m4%2Bx%2B65mm%2Bscrew%2Caps%2C349&sr=8-11&th=1)         |
| 4mm × 60mm Dowel Pins (20-pack)                           | For rollers (17)                                      | 1        | $8.49  | $8.49      | [Link](https://www.amazon.com/uxcell-Cylindrical-Mechanical-Manufacturing-Installation/dp/B0DRSK8KVQ/ref=sr_1_9?crid=38E0BU689LXYG&dib=eyJ2IjoiMSJ9.aWAMZjxppBFMB4swS3elqptbhqgfPEHFjv7UANpvRflSaR7oltgAewMVRKUmi28nBGiKpjB9eGG9r83ypni4jd7mdrFnFyDAfYK6q6U4CqLF0Dg65bZZuqaOGXCZhfmUMhpQIrBvVZ8JmjxMdclSA6Ae3QnXoJCJTWKEz7DGDxCzRW1PK_0bDKGqo5S2pnhOrKxCjreQGcCeR6cdjB0ijCKq56lMS9Z25IECV0ecoak.b-lbP_OmtE4Hn6jP2sVPMKea144GSHp2CcojCLu5ELo&dib_tag=se&keywords=4mm%2Bx%2B60mm%2Bpin&qid=1779226124&sprefix=4mm%2Bx%2B60mm%2Bpin%2Caps%2C146&sr=8-9&th=1)         |
| M4 × 5mm L × 6mm OD Threaded Inserts (50-pack)            | Inserts for housing and output disk connection (16)   | 1        | $7.69  | $7.69      | [Link](https://www.amazon.com/uxcell-Knurled-Printing-Threaded-Embedment/dp/B0CTCT5TXZ/ref=sr_1_3?crid=36X8EH1GT15B9&dib=eyJ2IjoiMSJ9._9icXmB270csr4R0w8gC7qbt91yv7losnPYT2O4WeFx2scWjZpMuW8SXrowR-gAgEKR9uFvw0vRhUNQPXx3JvmStA0B1GBjwSUaCDlJqG54esEab3M-RHDRhpTrZKMtvPCXfOhqdSFKD-G7zpdzruQMhYSZducSYoTt1Pa3CrIHfRH9iqNSMPui5wNZGDNJd1KzwWShe6LKgk9d3je7edw7xolkCqf7IpBzip5j8B58.o9WI-cboHdoBo71Kd9be3Dmk7lnBaYBXbqgI_D5j4Rc&dib_tag=se&keywords=M4%2Bx%2B5mm%2BL%2Bx%2B6mm%2BOD%2BThreaded%2BInserts%2B50%2Bpack&qid=1779247164&sprefix=m4%2Bx%2B5mm%2Bl%2Bx%2B6mm%2Bod%2Bthreaded%2Binserts%2B50%2Bpack%2Caps%2C184&sr=8-3&th=1)         |
| **Grand Total**                                           |                                                       |          |        | **$79.40** |              |

With filament supplied from the lab, the rest of the components came out to a total of $79.40. Added in extra costs of manufacturing and prototyping, this brings the total for this cycloidal drive to under $100. Note that many of these components are bought with higher quanities than needed so to build a second drive would only need a feew extra orders, bringing the projected cost of 2 fully assembled cycloidal drive to under $200.

<img width="400" height="480" alt="image" src="https://github.com/user-attachments/assets/6ea58544-1ffe-403d-a3e2-5ccd5c9a9279" />


## Results
- Reduction ratio: 17:1
- Maximum output torque: 40-50 Nm
- Number of design iterations: 20+
- Material: PETG
- Print time: 40+ hours (inclduing prototyping)

## Future Improvements
- Prototype with PLA and reduced infill
- Reduce housing wall width
- Finite element analysis
- Interference detection analysis

## Lessons Learned
This project strengthened my understanding of:

- Tolerance stack-up
- Design for additive manufacturing
- Bearing and shaft fits
- Iterative prototyping
- Mechanical power transmission
- Engineering tradeoff analysis
