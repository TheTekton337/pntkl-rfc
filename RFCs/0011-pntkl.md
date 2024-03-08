# pntkl - A React Native Application for Managing Custom Apps

## 1. Introduction

This RFC proposes the development of "pntkl," a React Native application designed to enable users to create, run, manage, and delete a list of custom applications and widgets they have developed using the pntkl-editor. The pntkl application aims to serve as a platform for managing these custom apps, which are developed in a React web application environment and integrated into React Native via a WebView component. The pntkl app will leverage the Communication Protocol and Standards established by our previous RFCs to ensure seamless interaction between the React Native environment and the React web-based IDE, pntkl-editor.

## 2. Background

As applications become increasingly modular and customizable, there is a growing need for tools that allow users to easily manage their customizations and app creations. The pntkl application addresses this need by providing a comprehensive solution for managing a portfolio of custom applications created with the pntkl-editor, a web-based IDE designed for crafting React and React-Native applications and customizations.

## 3. Objectives

- To provide an intuitive interface for managing a list of user-created applications and customizations.
- To enable CRUD operations (Create, Read, Update, Delete) for custom applications directly from the pntkl React Native application.
- To integrate the pntkl-editor within the pntkl app using a WebView component, allowing for seamless editing and preview of custom applications.
- To offer a user settings screen that includes profile and account information, global environment configuration, per-app configuration, and settings for development and customization experiences.

## 4. Features

### 4.1 Home Screen

- **Custom App List**: Display a list of custom applications created by the user with options to run, edit, or delete each application.
- **CRUD Operations**: Provide functionality to create a new custom app, edit existing apps' configurations or code, and delete apps from the list.

### 4.2 Custom App/Widget Editing and Preview

- **pntkl-editor Integration**: Embed the pntkl-editor within a WebView component, allowing users to edit and preview their custom applications and widgets within the pntkl app environment. Use an expandle set of floating action buttons, custom keyboard toolbar (iOS), or toolbar displayed above the keyboard (android) to facilitate a mobile-friendly coding experience.
- **Communication Protocol**: Utilize the established Communication Protocol and Standards for passing props and events between the React Native app and the pntkl-editor, ensuring seamless navigation and interaction.

### 4.3 Custom Dashboard Feature

- Offer a default dashboard configured with useful widgets available out of the box.
- Enable users to customize the dashboard theme and the selection and placement of widgets.
- Allow widget placements to be configured via JSON or through a drag-and-drop interface.
- Support widgets provided by the "pntkl" application itself and user-created widgets.

### 4.4 Widgets Screen - Custom Widget Management

- Similar to the Home Screen's app list, display a list of widgets created or configured by the user.
- Support CRUD operations for widgets: Create, Read, Update, and Delete.
- Enable users to create new widgets for use within their custom dashboards or share with the "pntkl" community.
- Facilitate the customization of widget properties and functionalities through "pntkl-editor."

### 4.5 User Settings Screen

- **Profile and Account Information**: Allow users to view and edit their profile details and manage account settings.
- **Global Environment Configuration**: Provide a section for users to set global environment configurations that all custom apps can use, such as API keys or global variables.
- **Per-App/Widget Configuration**: Enable users to set configurations specific to each custom app or widget, allowing for personalized app or widget behavior.
- **Development and Customization Settings**: Offer settings to customize the development environment and experience within the pntkl-editor, such as theme preferences or default code templates.

## 5. Technical Considerations

- **React-Codemirror**: Leverage react-codemirror for code editing functionalities within the pntkl-editor, providing a sophisticated coding interface.
- **CodeSandbox's Sandpack Project**: Utilize CodeSandbox's Sandpack project for code evaluation and preview within the pntkl-editor, enabling real-time feedback and testing of custom apps.
- **React Native WebView**: Implement the WebView component for embedding the pntkl-editor within the pntkl app, facilitating interaction between the web-based editor and the native application.

## 6. Implementation Plan

- **Phase 1a**: Develop the initial version of the pntkl app with basic CRUD operations and user settings screen.
- **Phase 1b**: Integrate the pntkl-editor using WebView, ensuring communication and event handling between the React Native and React web environments.
- **Phase 2**: Add advanced features such as global and per-app configurations, as well as enhanced customization settings for the development environment.
- **Phase 3**: Conduct user testing and iterate based on feedback to improve usability and functionality.

### 6.1 Development Approach

- Develop "pntkl" using React Native to ensure compatibility across multiple platforms.
- Implement "pntkl-editor" side-by-side as a React web application optimized for integration within React Native through WebView.
- Follow established communication protocols for interaction between the React Native application and the React web application.

### 6.2 User Interface and Experience

- Design the UI to be intuitive and user-friendly, adhering to the principles outlined in the UIXDG-RNRA.
- Prioritize the user experience in customization and management functionalities, ensuring smooth navigation and interaction.

### 6.3 Security and Data Management

- Adhere to security standards as defined in the ASS-RNRA, especially for user data handling and custom application management.
- Implement data persistence and state management for user customizations following the DPSM-RNRA guidelines, ensuring the integrity of user data across sessions.

## 7. Use Cases

- Users can create and manage custom applications tailored to their specific needs or interests.
- Users can utilize the customizable dashboard to have quick access to frequently used information or tools.
- Developers can streamline their workflow by managing and testing their custom applications within a single platform.

## 8. Conclusion

The pntkl application represents a significant step forward in enabling users to manage their custom applications and customizations efficiently. By providing a seamless integration between a React Native app and a web-based IDE, pntkl empowers users to create, edit, and manage their custom apps with ease, fostering innovation and personalization within the React and React-Native ecosystem.