# Field Specifications: Appointments

## MAIN SECTION/GROUPING

### Main Actions

| Num | Field Name | Display Label | Field Type | Description | Is Required? | Transaction or Source Table | Transaction or Source Column/s | LOVs (if any) | Default Value (if any) | Font Awesome Icon Name |
|-----|------------|---------------|------------|-------------|--------------|----------------------------|-------------------------------|---------------|------------------------|------------------------|
| 1 | Back | Back | Button | Takes user back to the previous step or page | N/A | N/A | N/A | N/A | N/A | N/A |
| 2 | Next | Next | Button | Takes user to the next page (except for Review Details step. For Review Details step, the Next button displays the Email Verification modal) | N/A | N/A | N/A | N/A | N/A | N/A |
| 3 | Cancel | Cancel | Button | Takes user back to facility profile page | NA | NA | NA | NA | NA | NA |

### Sub-Section/Grouping 1: Appointment Type

| Num | Field Name | Display Label | Field Type | Description | Is Required? | Transaction or Source Table | Transaction or Source Column/s | LOVs (if any) | Default Value (if any) | Font Awesome Icon Name |
|-----|------------|---------------|------------|-------------|--------------|----------------------------|-------------------------------|---------------|------------------------|------------------------|
| | Appointment Type | Select Appointment Type | Button | Allows patient to select from a list of appointment types created by admin. Under the Appointment Type name, the services included in that appointment type are displayed. | Yes | appt_types, appt_services, appt_type_services | appt_types.type_name, appt_services.service_name | appt_types in the facility calendar, services in the appointment type | NA | N/A |

### Sub-Section/Grouping 2: Choose Service

| Num | Field Name | Display Label | Field Type | Description | Is Required? | Transaction or Source Table | Transaction or Source Column/s | LOVs (if any) | Default Value (if any) | Font Awesome Icon Name |
|-----|------------|---------------|------------|-------------|--------------|----------------------------|-------------------------------|---------------|------------------------|------------------------|
| | Selected service | Choose the Service | Dropdown | Allows patient to select from a list of optional additional services to add to the appointment | No | appt_types, appt_services, appt_selected_services | appt_services.service_name | select-able services under the appointment type | None | N/A |

### Sub-Section/Grouping 3: Date and Time

| Num | Field Name | Display Label | Field Type | Description | Is Required? | Transaction or Source Table | Transaction or Source Column/s | LOVs (if any) | Default Value (if any) | Font Awesome Icon Name |
|-----|------------|---------------|------------|-------------|--------------|----------------------------|-------------------------------|---------------|------------------------|------------------------|
| | Date | Appointment Date | Calendar | Allows patient to select a date from available appointment dates | Yes | facility_calendars, calendar_operating_hours, calendar_appt_types, appt_types | Display day as availalable if facility is open on that day: calendar_operating_hours.is_closed, calendar offers the appointment type selected: calendar_appt_types.calendar_id | available dates in the calendar with appointment types selected by the patient | NA | NA |
| | Time | Appointment Time | Buttons | Allows patient to select a time from available time slots on the appointment day | Yes | calendar_operating_hours, appt_types, calendar_appt_types | Calculate slots based on calendar_operating_hours.opens_at and calendar_operating_hours.closes_at and the appt_types.duration_mins | available start times based on operating hours and duration per slot | NA | NA |

### Sub-Section/Grouping 4: Patient Details

| Num | Field Name | Display Label | Field Type | Description | Is Required? | Transaction or Source Table | Transaction or Source Column/s | LOVs (if any) | Default Value (if any) | Font Awesome Icon Name |
|-----|------------|---------------|------------|-------------|--------------|----------------------------|-------------------------------|---------------|------------------------|------------------------|
| | Appointment Type | Appointment Type | Read-only Text Column | Reflects the appointment type selected in previous section | NA | appointments | appointments.appt_type_id | NA | NA | NA |
| | Selected service | Service | Read-only Text Column | Reflects the additional service selected in previous section | NA | appointments, appt_selected_services | appt_selected_services.service_id for a specific appt_id | NA | NA | NA |
| | Date and time | Date and time | Read-only Text Column | Reflects the date and time selected in previous section | NA | appointments | appointments.appt_date, appointments.start_time | NA | NA | NA |
| | First name | First name | Textbox | Allows patient to enter their first name<br>- Minimum Length: 1<br>- Maximum Length: 50 characters<br>- Allowed Characters: Letters, spaces, hyphens (-), apostrophes ('), period (.) | Yes | appt_patients, appointments | appt_patients.first_name | NA | NA | NA |
| | Middle name | Middle name | Textbox | Allows patient to enter their middle name<br>- Minimum Length: 0<br>- Maximum Length: 50 characters<br>- Allowed Characters: Letters, spaces, hyphens (-), apostrophes ('), period (.) | No | appt_patients, appointments | appt_patients.middle_name | NA | NA | NA |
| | Last name | Last name | Textbox | Allows patient to enter their last name<br>- Minimum Length: 1<br>- Maximum Length: 50 characters<br>- Allowed Characters: Letters, spaces, hyphens (-), apostrophes ('), period (.) | Yes | appt_patients, appointments | appt_patients.last_name | NA | NA | NA |
| | Sex | Sex | Dropdown | Allows patient to enter their sex | Yes | appt_patients, appointments | appt_patients.sex | Male, Female, Other | None | NA |
| | Birthdate | Birthdate | Calendar | Allows patient to enter their birthdate | Yes | appt_patients, appointments | appt_patients.date_of_birth | NA | NA | NA |
| | Email | Email | Textbox | Allows patient to enter their email address<br>- Must be valid email address | Yes | appt_patients, appointments | appt_patients.email | NA | NA | NA |
| | Mobile number | Mobile number | Textbox | Allows patient to enter their mobile number<br>- Pre-filled with +63 (Philippines country code)<br>- 10 digits for mobile and starting with 9 | Yes | appt_patients, appointments | appt_patients.mobile | NA | NA | NA |
| | Patient attachments | Additional information | Button | Allows patient to upload attachments for the appointment<br>- Jpg, png, or pdf<br>- Max size per file 2 mb<br>- Maximum: 3 files | No | appointment_attachments, appointments | appointment_attachments | NA | NA | NA |
| | Patient note to facility | Send a message to the facility | Textbox (long) | Allows patient to enter a message to the facility<br>- Minimum: 0<br>- Maximum: 500 characters<br>- Allowable characters: any | No | appointments | appointments.note_from_patient | NA | NA | NA |

### Sub-Section/Grouping 5: Review Details

| Num | Field Name | Display Label | Field Type | Description | Is Required? | Transaction or Source Table | Transaction or Source Column/s | LOVs (if any) | Default Value (if any) | Font Awesome Icon Name |
|-----|------------|---------------|------------|-------------|--------------|----------------------------|-------------------------------|---------------|------------------------|------------------------|
| | Appointment Type | Appointment Type | Read-only Text Column | Reflects the appointment type selected in previous section | NA | appointments | appointments.appt_type_id | NA | NA | NA |
| | Selected service | Service | Read-only Text Column | Reflects the additional service selected in previous section | NA | appointments, appt_selected_services | appt_selected_services.service_id for a specific appt_id | NA | NA | NA |
| | Date and time | Date and time | Read-only Text Column | Reflects the date and time selected in previous section | NA | appointments | appointments.appt_date, appointments.start_time | NA | NA | NA |
| | First name | First name | Read-only Text Column | Reflects the first name entered in previous section | NA | appointments, appt_patients | appt_patients.first_name | NA | NA | NA |
| | Middle name | Middle name | Read-only Text Column | Reflects the middle name entered in previous section | NA | appointments, appt_patients | appt_patients.middle_name | NA | NA | NA |
| | Last name | Last name | Read-only Text Column | Reflects the last name entered in previous section | NA | appointments, appt_patients | appt_patients.last_name | NA | NA | NA |
| | Sex | Sex | Read-only Text Column | Reflects the sex selected in previous section | NA | appointments, appt_patients | appt_patients.sex | NA | NA | NA |
| | Birthdate | Birthdate | Read-only Text Column | Reflects the date of birth selected in previous section | NA | appointments, appt_patients | appt_patients.date_of_birth | NA | NA | NA |
| | Email | Email | Read-only Text Column | Reflects the email entered in previous section | NA | appointments, appt_patients | appt_patients.email | NA | NA | NA |
| | Mobile number | Contact number | Read-only Text Column | Reflects the mobile number entered in previous section | NA | appointments, appt_patients | appt_patients.mobile | NA | NA | NA |
| | Patient attachments | Uploaded documents | Read-only Text Column | Reflects the attachments uploaded | NA | appointments, appointment_attachments | appointment_attachments | NA | NA | NA |
| | Patient note to facility | Message to the facility | Read-only Text Column | Reflects the note entered in the previous section | NA | appointments | appointments.note_from_patient | NA | NA | NA |

### Sub-Section/Grouping 5.1: Email Verification Modal

| Num | Field Name | Display Label | Field Type | Description | Is Required? | Transaction or Source Table | Transaction or Source Column/s | LOVs (if any) | Default Value (if any) | Font Awesome Icon Name |
|-----|------------|---------------|------------|-------------|--------------|----------------------------|-------------------------------|---------------|------------------------|------------------------|
| | Email | We've sent a verification code to your email | Read-only Text Column | Reflects the email entered in previous section | NA | appointments, appt_patients | appt_patients.email | NA | NA | NA |
| | Verification code | Enter the verification code to confirm your appointment request | Textbox | Allows patient to enter the OTP | Yes | NA | NA | NA | NA | NA |
| | Resend | Resend | Link | Resends a new OTP to the email provided | NA | NA | NA | NA | NA | NA |
| | Submit new appointment | Submit | Button | Finalizes the appointment request and commits inputs to the appt_patients and appointments table | NA | NA | NA | NA | NA | NA |

### Sub-Section/Grouping 5.2: Appointment Request Submitted/Confirmation UI

| Num | Field Name | Display Label | Field Type | Description | Is Required? | Transaction or Source Table | Transaction or Source Column/s | LOVs (if any) | Default Value (if any) | Font Awesome Icon Name |
|-----|------------|---------------|------------|-------------|--------------|----------------------------|-------------------------------|---------------|------------------------|------------------------|
| | Appointment status | Status | Read-only Text Column | Reflects the status of the appointment | NA | appointments | appointments.status | scheduled, confirmed, cancelled, no_show | scheduled | NA |
| | Appointment Type | Appointment Type | Read-only Text Column | Reflects the appointment type selected in previous section | NA | appointments | appointments.appt_type_id | NA | NA | NA |
| | Selected service | Service | Read-only Text Column | Reflects the additional service selected in previous section | NA | appointments, appt_selected_services | appt_selected_services.service_id for a specific appt_id | NA | NA | NA |
| | Date and time | Date and time | Read-only Text Column | Reflects the date and time selected in previous section | NA | appointments | appointments.appt_date, appointments.start_time | NA | NA | NA |
| | Back to facility profile | Back to facility profile | Button | Takes user back to facility profile page | NA | NA | NA | NA | NA | NA |
| | Request another appointment | Request another appointment | Button | Takes user back to begin input of a new appointment request (Grouping 1) | NA | NA | NA | NA | NA | NA |