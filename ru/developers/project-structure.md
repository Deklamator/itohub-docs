# Project Structure

The `ito_web` project is based on Create React App (CRA) and has a structure similar to the Feature-Sliced Design methodology, which ensures good organization and scalability.

Below is the structure of key directories inside the `src/` folder:
src/
├── app/
│   ├── providers/  # Wrappers and providers (Router, Redux, TON Connect)
│   └── styles/     # Global styles and Tailwind styles
├── components/     # Reusable UI components (buttons, inputs, modals)
├── hooks/          # Global custom hooks (useAuth, useDealPolling)
├── pages/          # Main application pages (HomePage, DealPage, ProfilePage)
├── services/       # API interaction logic (AuthService, DealService)
├── ton/            # Everything related to the TON blockchain (transaction creation functions)
├── types/          # Global TypeScript types and interfaces
└── utils/          # Helper utilities (logger, date formatters)
### **Key Folder Descriptions:**

* **`app`**: The core of the application. Global providers and styles are initialized here.
* **`components`**: The "building blocks" for the interface. This is where universal components used across different pages are stored.
* **`hooks`**: Custom React hooks that encapsulate complex logic (e.g., authentication, regular server polling).
* **`pages`**: Each folder here represents a separate screen or route in the application. Pages are assembled from components.
* **`services`**: The service layer responsible for all communication with the backend.
* **`ton`**: An isolated module for all logic related to the TON blockchain: building transactions, interacting with contracts.
* **`types`**: A centralized location for storing all data models (TypeScript types).
* **`utils`**: Small helper functions used in various parts of the project.