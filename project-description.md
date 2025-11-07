# Test Project Outline – Module B – Dynamic Website with Server-Side Rendering

## Competition time

4 hours

## Introduction

For the promotion of cycling in the city, the company **VelOrda** has launched a project to create a safe and scalable online platform for managing bicycle rentals. Your development team has been tasked with building this service taking into account modern security and usability standards.

The goal of this module is to create an administrator panel — a server-side rendered admin dashboard where clients can manage bicycle rentals.

Since the admin panel will be publicly accessible for viewing, it must follow OWASP guidelines.

## General Description of Project and Tasks

You will create a server-side rendered (SSR) admin dashboard for managing a bicycle rental system. The system must handle user authentication, bicycle category management, bicycle inventory, rental conditions, pricing tariffs, booking history, moderation applications, and promotional codes.

The client will provide example data in CSV format which you must use. However, this data might not be normalized and it is up to you to design a proper database schema and import it according to Third Normal Form (3NF).

Module B must be implemented using a server-side framework. You can optionally use JavaScript to enhance the user experience, but the initial content of each page must be rendered on the server.

### Technical Requirements

- Must work in the latest version of Google Chrome browser
- Use any CSS framework or your own styles, but keep branding consistent
- Clear navigation allowing access to all features
- Admin section must have a clear and polished design (UI/UX will be evaluated)
- While design is not the primary focus, the interface should be professional and user-friendly

### Security Requirements

All implementations must follow OWASP security guidelines:

- **CSRF Protection**: Implement CSRF tokens on every form or action (POST/PUT/DELETE)
- **XSS Prevention**: Escape/encode user input in views to avoid cross-site scripting attacks
- **SQL Injection Prevention**: Use parameterized queries or rely on an ORM to prevent SQL injection

### Database Requirements

- Design your database schema following Third Normal Form (3NF)
- Provide a database dump file named `DB-dump.sql` in the project's database folder
- Provide an ER (Entity-Relationship) diagram image named `ERD.png` in the project's database folder
- Import and normalize the provided CSV data files

## Requirements

The goal of the website is to provide a comprehensive admin dashboard for the VelOrda bicycle rental platform. Administrators must be able to manage bicycle categories, individual bicycles, rental conditions, pricing tariffs, view rental history with export capabilities, moderate rental applications, and create promotional codes.

### Authentication

All pages are protected from unauthorized users. Login must be done using either email or phone number together with a password.

The following accounts must be created:

- Email: `user1@gmail.com`<br>Phone: +77777777771<br>Password: `ts2025u1`
- Email: `user2@gmail.com`<br>Phone: +77777777772<br>Password: `ts2025u2`

It must be possible to log out from the account.

### Categories

After successful login, the user is redirected to the category list page.

The page displays a list of bicycle categories belonging to the authorized user only.

User can:

- Create a new category (only the name field is required).
- Edit an existing category (only the name can be changed).
- Delete a category only if it contains no bicycles.

### Bicycles

The page displays all bicycles related to the selected category.

The user can add, edit, delete, or change the status (available, unavailable) of a bicycle.

Bicycle image upload must be implemented using drag-and-drop (DnD).

If a bicycle is already booked or currently rented, its status cannot be changed to `unavailable`.

A bicycle has the following attributes:

| Field       | Description                     |
| ----------- | ------------------------------- |
| Name        | Maximum length: 100 characters  |
| Description | Optional field                  |
| Wear        | Percentage of wear (default: 0) |
| Image       | Optional field                  |

When adding a bicycle, you can specify its quantity (copies). It is possible to create a copy of this bicycle with default parameters. Each bicycle must have a unique slug based on its name. If a bicycle with the same name already exists, a free sequential number is appended to the end. For example: super-bicycle → super-bicycle-01.

A bicycle can only be deleted if its status is `unavailable`.

The coordinates (x, y) of the bicycle’s image center are automatically and randomly generated (with a 10px offset from each other) on a 5000x5000 map. All bicycles must be visible on the map.

The image size of each bicycle on the map is fixed:

- Width: 50px
- Height: 50px

---

### Rent Conditions

For each category, rental conditions can be added depending on the weather and/or the user’s rating.

The rental conditions apply to all bicycles within the category.

Rental conditions:

- If weather is selected, the allowed values must be chosen from the list (one or more).
- If user rating is selected, the minimum rating must be specified (e.g., 4.70).

Available weather values:

- Clear
- Fog
- Rain
- Snow

### Tariffs

For each category, one or more tariffs can be created.
Tariffs are displayed with a name, type (fixed or dynamic), and price (in tenge) per minute. Duplicate tariffs cannot be created.

If a tariff has a dynamic type, a minimum and maximum price must also be set.

A tariff can be archived, but it must still appear in the general list in a different form (e.g., in another color).

### History

On a separate page, the bicycle rental history can be viewed.

The list must display the following data:

- Name and phone number of the renter
- Rental start date
- Rental end date
- Wear percentage at the end of the rental with user-submitted photos
- Final price
- Given rating (nullable)

The list can be filtered by date.

Pagination must also be implemented (10 items per page). The following navigation buttons are required:

- Previous
- Next
- Page numbers (with an ellipsis if there are more than 3 pages)

The user can export the history (with the applied filter) as a CSV file by clicking the `Export` button. The exported file must include all data displayed in the list on the page.

File name pattern: exports_history-Y-m-d.csv (for example, `exports_history_2025-10-06.csv`).

### Applications

This page displays requests for moderating your bicycles within the category.

Each request must contain the following applicant data:

- Name
- Phone number
- Email

The user can approve or reject a request.

### Promo Codes

The user can create a unique promo code for using their bicycles within a category.
The promo code must consist of a random string (5 to 10 characters) containing only uppercase letters and digits.

Promo code attributes:

- Expiration time
- Free usage minutes or discount percentage

The user can delete a promo code.

### Database and Example Data

The database schema is not provided, so you must design it yourself, taking Third Normal Form (3NF) into account.

Import the data from the provided CSV files into your database, normalize them, and provide a dump for testing. The following CSV files are provided in the `assets/data/` folder:

- `users.csv` - User account data
- `categories.csv` - Bicycle category data
- `bicycles.csv` - Bicycle inventory data
- `bookings.csv` - Rental booking history
- `tariffs.csv` - Pricing tariff data
- `applications.csv` - Moderation application requests

Example bicycle images are also provided in `assets/images/`.

## Assessment

Module B will be assessed using the latest version of Google Chrome browser. Various security aspects will be checked including CSRF protection, XSS prevention, and SQL injection prevention. The UI/UX will be evaluated for usability and professionalism, though design aesthetics are not the primary focus. The database dump and ER diagram will be assessed for correctness, normalization (3NF compliance), and completeness.

## Mark distribution

The table below outlines how marks are broken down and how they align with the WorldSkills Occupation Standards (WSOS). Please read the Technical Description for a full explanation of the WorldSkills Occupation Standards.

| WSOS SECTION | Description                            | Points |
| ------------ | -------------------------------------- | ------ |
| 1            | Work organization and self-management  | 1.0    |
| 2            | Communication and interpersonal skills | 0.5    |
| 3            | Design Implementation                  | 3.0    |
| 4            | Front-End Development                  | 2.5    |
| 5            | Back-End Development                   | 16.0   |
|              |                                        |        |
| **Total**    |                                        | 23.0   |
