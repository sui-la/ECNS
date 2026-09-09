## EnGenius Certified Wireless Professional

## WLAN Fundamentals
##### Electromagnetic Wave
- frequency, number of oscillation per sec
- wavelength, length of single oscillation
- speed of light
- Frequency and wavelength have an inverse relationship, relative to the speed of light (c): 
f=c/λ
<img width="818" height="594" alt="image" src="https://github.com/user-attachments/assets/29dba1ec-cdf9-4310-bc43-ed4b5afd746e" />

##### Modulation
- Amplitude Modulation (AM): Change the amplitude (i.e. power) of the signal over time
- Frequency Modulation (FM): Change the frequency (i.e. wavelength) of the signal over time
- Phase Modulation (PM): Change the phase of the signal over time
<img width="798" height="562" alt="image" src="https://github.com/user-attachments/assets/68907467-277f-4c50-893d-e5db2912912f" />

##### Unit of Measurement
- decibals
- Power levels in Wi-Fi: 1000 mW to 10^-9 mW
- Types of Power Measurement:
  - dBm: Absolute measure of power in decibels (relative to milliwatts, where 0 dBm = 1 mW)
  - dB: Relative comparison of two power values
  - dBi: Relative gain of signal strength of an antenna (relative to a theoretical isotropic radiator
- Law of 3 dB
  - +3 dB = 2x power
  - -3 dB = 1/2 power
  - eg: 16 db = 16 mW -> 19 db = 32 mW...
- Law of 10 dB
  - +10 dB = 10x power
  - -10 dB =  0.1x power
  - eg: 10 db = 10 mW -> 20 db = 100 mW
 
##### Signal Degration
1. thermal noise
- unavoidable noice, comes from the vibration of the atoms(>absolute zero degree)
- N dbm (Thermal noise in dBm) =10 log 10(1000 kB (Boltzmann constant) Temp) + 10 log 10(∆f (channel size, Hz))
2. free space path loss (FSPL)
- degradation of electromagnetic waves signal strength when propagates through free space
- distance between a transmitter and receiver
- $$FSPL_{\text{dB}} = 20 \log_{10}(d) + 20 \log_{10}(f) + 20 \log_{10}\left(\frac{4\pi}{c}\right)$$
3. Attenuation
- loss of electromagnetic signals from interaction with objects in the environment
- Function of the material type and the wavelength:
  - Absorption: Energy absorbed by the material
  - Reflection: Energy reflected by the material (creates multipath signals)
- Lower frequency signals propagate through materials more easily (i.e. less loss) than higher frequency signals
<img width="736" height="425" alt="image" src="https://github.com/user-attachments/assets/1d21efe7-44c8-45b7-8bc7-5cda4f7572c4" />

3. Diffraction
- cause bending of eletromagnetic waves
4. Fresnel Zone (fray-NELL)
- a electromagnetic wave signal between point-to-point/multi that does not have any obstacles (line of sight)
- calculation: $$R_n = \sqrt{\frac{n \lambda d_1 d_2}{d_1 + d_2}}$$

##### Link Budget
- The link budget is estimated based on the following factors:
  - **EIRP: Effective isotropic radiated power**
    **- Transmitter power
    - Transmitter antenna gain
    - Transmitter antenna cable / connector losses
  - Free space path loss
  - Attenuation in path (e.g. walls, windows, etc.)
  - Receiver antenna gain
  - Receiver antenna cable / connector losses**
- **Received Signal Strength Indicator (RSSI)**
  - Measured signal strength at the receiver
- **Receive Sensitivity**
  - Minimum signal strength that the receiver can interpret a signal at a particular modulation
- **Fade Margin / SNR (signal to noise ratio)**
  - Difference between the link budget and the receive sensitivity (a.k.a. signal to noise ratio)
  - Good performance requires > 15 - 20 dB margin
 
 ##### Contention
- wired and wireless have same travel speed
- wired have better throughput result
- collision may occur when many devices transmit data
- **wired:**
  - full-duplex, send and receive same time
  - detect collision, pause, wait the wire clear, resume 
- **wireless:**
  - half-duplex, either send or receive same time
  - cannot detect collision when transmit data
- **Avoidance**
  - reserve a connection lifetime
  - send frame
  - received ACK?
  - no -> collision, vise versa

##### Data Rate
- connection or link-speed in a given period of time
- may be affect by AP, wireless adapter of connecting device, and RSSI to name a few

##### Standards and Regulations
* **Regulatory Bodies (FCC & CE):** 
  * Enforce rules and allocate radio spectrum for radio, television, wire, satellite, and cable communications.
  * **Licensed Spectrum:** Organizations pay to use specific frequencies in a designated area (e.g., cellular networks).
  * **Unlicensed Spectrum:** Free for public use (e.g., Wi-Fi bands) provided equipment complies with power limits and interference rules.

* **Wi-Fi Alliance:**
  * An industry association of over 350 manufacturers that conducts standardized interoperability testing.
  * Certifies key features including Quality of Service (**WMM**), Power Saving (**WMM-PS**), Security (**WPA/WPA2/WPA3**), and Voice over Wi-Fi (**VoWiFi**).

* **Standards Organizations (IEEE & ETSI):**
  * **IEEE:** Defines core technical standards for Wi-Fi technologies.
  * **ETSI:** Establishes Harmonized European Standards required for European regulations.
  * **Band Allocation:** Opening new frequency ranges (such as the $6\text{ GHz}$ band for Wi-Fi 6E) requires official approval and rule changes from these regulatory agencies.
 
  
