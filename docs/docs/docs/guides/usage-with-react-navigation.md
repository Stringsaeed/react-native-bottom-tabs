# Usage with React Navigation

:::warning
To use this navigator, ensure that you have [`@react-navigation/native` and its dependencies (follow this guide)](https://reactnavigation.org/docs/getting-started).
:::

```tsx
import {createNativeBottomTabNavigator} from 'react-native-bottom-tabs/react-navigation';

const Tabs = createNativeBottomTabNavigator();

function NativeBottomTabs() {
  return (
    <Tabs.Navigator>
      <Tabs.Screen
        name="index"
        options={{
          title: "Home",
          tabBarIcon: () => ({ sfSymbol: "house" }),
        }}
      />
      <Tabs.Screen
        name="explore"
        options={{
          title: "Explore",
          tabBarIcon: () => ({ sfSymbol: "person" }),
        }}
      />
    </Tabs.Navigator>
  );
}
```

### Props

The `Tab.Navigator` component accepts following props:

#### `id`

Optional unique ID for the navigator. This can be used with `navigation.getParent` to refer to this navigator in a child navigator.

#### `initialRouteName`

The name of the route to render on first load of the navigator.

#### `screenOptions`

Default options to use for the screens in the navigator.

#### `labeled`

Whether to show labels in tabs. Defaults to true.

#### `disablePageAnimations`

Whether to disable page animations between tabs. (iOS only)

#### `scrollEdgeAppearance`

Describes the appearance attributes for the tabBar to use when an observable scroll view is scrolled to the bottom. (iOS only)

Available options:
- `default` - uses default background and shadow values.
- `transparent` - uses transparent background and no shadow.
- `opaque` - uses set of opaque colors that are appropriate for the current theme

Note: It's recommended to use `transparent` or `opaque` without lazy loading as the tab bar background flashes when a view is rendered lazily.
#### `sidebarAdaptable`

A tab bar style that adapts to each platform. (Apple platforms only)

Tab views using the sidebar adaptable style have an appearance
- iPadOS displays a top tab bar that can adapt into a sidebar.
- iOS displays a bottom tab bar.
- macOS and tvOS always show a sidebar.
- visionOS shows an ornament and also shows a sidebar for secondary tabs within a `TabSection`.


### Options

The following options can be used to configure the screens in the navigator. These can be specified under `screenOptions` prop of `Tab.navigator` or `options` prop of `Tab.Screen`.

#### `title`

Title text for the screen.

#### `tabBarLabel`

Label text of the tab displayed in the navigation bar. When undefined, scene title is used.

#### `tabBarIcon`

Function that given { focused: boolean } returns ImageSource or AppleIcon to display in the navigation bar.

Note: SF Symbols are only supported on Apple platforms.

```tsx
<Tab.Screen
  name="Albums"
  component={Albums}
  options={{
    tabBarIcon: () => require('person.png'),
    // or
    tabBarIcon: () => ({ sfSymbol: 'person' }),
  }}
/>

```

#### `tabBarBadge`

Badge to show on the tab icon.

#### `lazy`

Whether this screens should render the first time it's accessed. Defaults to true. Set it to false if you want to render the screen on initial render.
