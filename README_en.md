<div align="right">
  🌍 <a href="README.md">Español</a> | <strong>English</strong>
</div>

# 🚘 Urban Routes: Test Design and Requirements Analysis (Car Sharing)

![Project](https://img.shields.io/badge/Project-Test_Design-blue) ![Status](https://img.shields.io/badge/Status-Completed-success) ![Tools](https://img.shields.io/badge/Tools-Draw.io_/_Google_Sheets-green) ![Techniques](https://img.shields.io/badge/Techniques-Boundary_Values_/_Equivalence_Classes-orange)

## 📌 Project Summary (STAR Methodology)

*   **Situation:** The **Urban Routes** application needed to launch a new "Car Sharing" feature. It was critical to ensure that the "Add Driver's License" form correctly validated user data, and that the dynamic algorithm for calculating price and trip duration (based on departure time and distance) functioned without mathematical errors.
*   **Task:** Break down business requirements, identify "grey areas" (ambiguities), and design the testing architecture from scratch using formal test design techniques.
*   **Action:** 
    * Modeled the interface and behavior of the licenses module using a **Mind Map**.
    * Designed a **Flowchart** to map the vehicle speed selection logic according to time slots (e.g., 45 km/h from 00:01 to 08:00).
    * Applied **Equivalence Classes and Boundary Value Analysis** techniques to stress the "Name" and "Last Name" fields (validating lengths of 2 to 14 characters, use of hyphens, and non-Latin characters).
    * Wrote mathematical Test Cases to validate the backend formula: `T (duration) = S (distance) / V (speed)` and `Cost = T * price per minute`.
*   **Result:** Delivered a robust test matrix that guaranteed exhaustive coverage in both UI validations and backend logic. The strict application of boundary values prevented calculation errors in production and vulnerabilities in user data entry.

![Flowchart](assets/02_Mapa Mental.jpg)

---

## 🛠️ Technical Showcase: Test Design Techniques

To maximize coverage while minimizing redundancy, I use equivalence partitioning. Here is an excerpt from my analysis for the "Name" field in the driver's license form:

| Class Name | Boundaries | Test Data Inside the Class | Test Data at the Boundaries |
| :--- | :--- | :--- | :--- |
| Valid Length (2 to 14 characters) | `Range: 2, 14` | 10 Characters - "Roque Ivan" | `Li: 2`, `Ls: 14`, `Li-1: 1`, `Ls+1: 15` |
| Special Characters (Invalid) | `Set` | "Auxili@dor13" | N/A |
| Non-Latin Characters (Valid) | `Set` | "María" (Use of accents) | N/A |



---
*🧑‍💻 Technical Profile: María Auxiliadora Vélez Mendoza - QA Engineer*
