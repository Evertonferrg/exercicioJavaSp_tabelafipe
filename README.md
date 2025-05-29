🚗 TABELA FIPE Value Search API (Java & Spring)
✨ Project Overview
This project is a Spring Boot application developed as part of the Java & Spring Boot course at Alura, specifically for the ONE G8 cohort. It provides a robust RESTful API to query vehicle values using the public FIPE API. A key enhancement of this project, distinguishing it from the raw FIPE API, is the implementation of custom search mechanisms to allow for more granular searches by model and year, which are not directly supported by the original API's initial structure.

🚀 Features
Vehicle Search by FIPE Code: Look up precise vehicle values using the unique FIPE code.
Brand Listing: Retrieve a comprehensive list of available vehicle brands.
Dynamic Model Search: Custom-built logic to find models associated with a specific brand, offering more detailed results than the direct API.
Year-Specific Search: Advanced filtering to obtain available years for a given brand and model, providing refined search capabilities.
Detailed Value Retrieval: Obtain the exact FIPE value for a specific vehicle (brand, model, year combination).
RESTful API: Offers a clean, intuitive, and easy-to-integrate API.
🛠️ Technologies Used
Core Technologies
Java 
External API
(Data provided by https://deividfortuna.github.io/fipe/)

💡 How it Was Built (Step-by-Step)
This project was developed incrementally, focusing on understanding RESTful principles and external API integration:

Project Initialization: Started with a Spring Boot project generated via Spring Initializr, including Spring Web and Lombok dependencies.
API Client Setup: Implemented a service class (ConsumeApi or similar) responsible for making HTTP requests to the FIPE API and handling responses.
Data Modeling: Created Java records/classes (e.g., Brand, Model, VehicleValue) to map the JSON responses from the FIPE API into strongly typed objects.
Basic API Endpoints: Developed initial REST controllers (FipeController) to expose basic FIPE functionalities, such as listing brands.
Custom Model/Year Logic (The Core Enhancement):
Iterative Search: Since the FIPE API doesn't directly offer a single endpoint to list all models/years for a given brand/model, a custom mechanism was implemented. This involved:
Fetching a generic list of vehicles for a given brand (e.g., "carros").
Iterating through these generic results to extract and consolidate unique models and years available.
This approach effectively "builds" the model/year distinctions by processing the available data, providing a more user-friendly search experience.
This logic significantly enhanced the API's usability beyond what the raw FIPE API provided, allowing for granular searches by model and year.
Error Handling & Robustness: Implemented basic error handling for API calls and data processing.
Testing (Implicit/Manual): Throughout development, endpoints were manually tested using tools like Insomnia or Postman to ensure correct data retrieval and processing.
⚙️ How to Run Locally
To get this project up and running on your local machine, follow these steps:

Prerequisites: Ensure you have Java 17+ and Maven installed.

Clone the Repository:

Bash

git clone <YOUR_REPOSITORY_URL>
cd <YOUR_PROJECT_FOLDER_NAME>
Build the Project:
Use Maven to build the project. This will download all necessary dependencies.

Bash

mvn clean install
Run the Application:
You can run the Spring Boot application using Maven:

Bash

mvn spring-boot:run
Alternatively, you can run the generated JAR file:

Bash

java -jar target/<YOUR_PROJECT_NAME>-<VERSION>.jar
The application will typically start on http://localhost:8080.

📖 API Endpoints
Here are some example API endpoints exposed by this application:

Get all brands:
GET /api/fipe/brands
Example Response: [ { "code": "1", "name": "Chevrolet" }, ... ]

Get models for a specific brand (e.g., Chevrolet - code 1):
GET /api/fipe/brands/1/models
Example Response: [ { "code": "1001", "name": "Onix" }, { "code": "1002", "name": "Tracker" }, ... ]
(This endpoint leverages the custom logic to provide distinct models.)

Get years for a specific model (e.g., Onix - code 1001 of Chevrolet - code 1):
GET /api/fipe/brands/1/models/1001/years
Example Response: [ { "code": "2023-1", "name": "2023 Gasolina" }, { "code": "2022-3", "name": "2022 Diesel" }, ... ]
(This endpoint also uses the custom logic to determine available years.)

Get FIPE value for a specific vehicle (e.g., Onix 2023 Gasolina):
GET /api/fipe/brands/1/models/1001/years/2023-1/value
Example Response: { "valor": "R$ 75.000,00", "marca": "Chevrolet", "modelo": "Onix", "anoModelo": 2023, ... }

📚 Alura ONE - G8 Cohort
This project was developed as a practical exercise during the Oracle Next Education (ONE) program by Alura, specifically for the G8 cohort. It demonstrates the skills acquired in Java and Spring Boot for building robust backend applications and integrating with external APIs.

🤝 Contributing
Contributions are welcome! If you have suggestions, bug reports, or want to contribute code, please feel free to open an issue or submit a pull request.


📞 Contact
Seu Nome/Nickname: Evertonferrg
Seu Email (Opcional): evertonferrg@gmail.com
Remember to Customize:
Replace all placeholders like <YOUR_REPOSITORY_URL>, <YOUR_PROJECT_FOLDER_NAME>, etc., with your actual project details.
Create a LICENSE file in your repository if you choose the MIT License.
Update the API endpoints in the API Endpoints section to precisely match what your Spring Boot application exposes.
This detailed README should professionally present your project, highlight your key achievements (especially the custom search logic), and provide all necessary information for users and potential collaborators.

