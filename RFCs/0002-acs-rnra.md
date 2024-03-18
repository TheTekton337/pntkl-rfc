# Application Configuration Standard for React and React Native Applications (ACS-RNRA)

## 1. Introduction

This RFC proposes an Application Configuration Standard for React and React Native Applications (ACS-RNRA) to ensure a seamless, efficient, and standardized approach for passing configuration data between React and React Native applications. Leveraging the Communication Protocol with Turbo Module Integration for React and React Native Applications (CP-RNRA), this standard focuses on optimizing the configuration and setup of React components and their equivalents in React Native through a unified, structured data format.

## 2. Background

As web and mobile development converge, particularly through frameworks like React and React Native, the need for a unified approach to configuring components across these platforms becomes increasingly critical. Configuration data, such as that for the react-codemirror editor, must be passed efficiently and correctly interpreted across environments. The CP-RNRA, with its support for direct and typed data passing, offers a foundation upon which this configuration standard is built.

## 3. Objectives

- Define a universal configuration object structure that is compatible with both React and React Native applications.
- Utilize the CP-RNRA, particularly its Turbo Module integration, for efficient data passing of configuration objects.
- Ensure that the configuration standard supports a broad range of component types and configuration scenarios.
- Promote ease of integration, clarity, and consistency in configuring React components across web and native platforms.

## 4. Configuration Standard

### 4.1 Configuration Object Structure

A application configuration object (ACO) should adhere to the following structure:

```json
{
  "componentType": "String identifying the component",
  "configuration": {
    // Component-specific configuration properties
  },
  "lifecycleEvent": "Applicable lifecycle event for configuration application"
}
```

### 4.2 Lifecycle Event Integration

Configuration objects should be passed during appropriate lifecycle events, as identified within the CP-RNRA framework:

- **initialize**: When a component is being initialized.
- **mount**: At the component's mounting stage in the application.
- **update**: When updating the component's configuration.
- **unmount**: Prior to the component's removal or disposal.

### 4.3 Utilizing Turbo Modules for Configuration Passing

To pass a configuration object from a React Native application to a React web component (or vice versa), utilize the direct and typed data passing capabilities provided by Turbo Modules:

**React Native Example (Using Turbo Modules):**

```javascript
import { NativeModules } from 'react-native';

const { MyTurboModule } = NativeModules;

MyTurboModule.handleEvent({
  type: 'setValue',
  eventType: 'updateConfiguration',
  payload: {
    componentType: 'react-codemirror',
    configuration: {
      // Configuration properties
    },
    lifecycleEvent: 'mount'
  },
});
```

**React Example (Handling Configuration):**

The web component should be designed to receive and apply the configuration object based on the specified lifecycle event:

```javascript
useEffect(() => {
  // Logic to receive and apply configuration object
}, [configuration]);
```

### 4.4 Handling Without Turbo Modules

For environments or situations where Turbo Modules are not available or applicable, the standard bridge can be used for passing configuration objects between React and React Native applications. This approach utilizes the traditional `postMessage` and `onMessage` communication methods:

**React Native to Web (WebView):**

```javascript
// React Native
webViewRef.current.postMessage(JSON.stringify({
  componentType: 'react-codemirror',
  configuration: {
    // Configuration properties
  },
  lifecycleEvent: 'mount'
}));
```

**Web (Handling Configuration):**

```javascript
// In the web content loaded in WebView
window.addEventListener('message', (event) => {
  const data = JSON.parse(event.data);
  if (data.componentType === 'react-codemirror') {
    // Apply configuration based on the data
  }
});
```

This method should be used with caution and include additional validation and security checks, as it involves passing messages through a less direct channel.

### 4.5 Security and Efficiency Considerations

Follow the CP-RNRA's guidelines on security and efficiency to ensure safe, performant communication of configuration data:

- Validate configuration sources and integrity.
- Sanitize configuration data to prevent injection attacks.
- Optimize message sizes and handle high-frequency configuration updates judiciously.

## 5. Use Cases

- **Dynamic Configuration**: React Native applications dynamically configuring React web components in real-time, such as changing themes, functionalities, or behaviors based on user interaction.
- **Component Initialization**: Setting initial configuration for components like react-codemirror when they are loaded within a React Native WebView or directly in a React application.

## 6. Conclusion

The proposed Universal Configuration Standard for React and React Native Applications leverages the strengths of CP-RNRA to offer a structured, efficient, and secure method for passing configuration data across web and native boundaries. By adhering to this standard, developers can ensure that components are configured consistently, irrespective of the platform, enhancing both developer experience and application performance.