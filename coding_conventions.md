This guide is inspired and inherited from [ribot guidelines](https://github.com/ribot/android-guidelines/blob/master/project_and_code_guidelines.md) with some my changes to apply to my projects.

# 1 Coding naming conventions
## 1.1 Android Resources naming

Resources file names are written in **lowercase_underscore**.

### 1.1.1 Drawable files

Naming conventions for drawables:


| Asset Type   | Prefix            |		Example                  |
|--------------| ------------------|-----------------------------|
| Action bar   | `ab_`             | `ab_stacked.9.png`          |
| Button       | `btn_`	           | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon (png)   | `ic_`	           | `ic_star.png`               |
| Vector       | `vt_`             | `vt_facebook.xml`           |
| Menu         | `menu_	`          | `menu_submenu_bg.9.png`     |
| Notification | `notification_`	 | `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |
| Selectors    | `selector_`       | `selector_btn_blue.xml`     |
| Shape        | `shape_`          | `shape_circle_green.xml`    |

Naming conventions for icons (taken from [Android iconography guidelines](http://developer.android.com/design/style/iconography.html)):

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

Naming conventions for selector states:

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |

### 1.1.2 Layout files

Layout files should match the name of the Android components that they are intended for but moving the top level component name to the beginning. For example, if we are creating a layout for the `SignInActivity`, the name of the layout file should be `activity_sign_in.xml`.

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `view_stats_bar.xml`       |

A slightly different case is when we are creating a layout that is going to be inflated by an `Adapter`, e.g to populate a `ListView`. In this case, the name of the layout should start with `item_`.

Note that there are cases where these rules will not be possible to apply. For example, when creating layout files that are intended to be part of other layouts. In this case you should use the prefix `view_`.

### 1.2.3 Menu files

Similar to layout files, menu files should match the name of the component. For example, if we are defining a menu file that is going to be used in the `UserActivity`, then the name of the file should be `activity_user.xml`

A good practice is to not include the word `menu` as part of the name because these files are already located in the `menu` directory.

### 1.2.4 Values files

Resource files in the values folder should be __plural__, e.g. `strings.xml`, `styles.xml`, `colors.xml`, `dimens.xml`, `attrs.xml`, `arrays.xml`.

### 1.2.5 Resource ID naming

IDs should be prefixed with the name of the element in lowercase underscore. For example:

| Element                              | Prefix            |
| -------------------------------------| ----------------- |
| `TextView`                           | `text_`           |
| `ImageView`                          | `image_`          |
| `Button`                             | `button_`         |
| `Menu`                               | `menu_`           |
| `EditText`                           | `input_`          |
| `Layouts` (e.g. LinearLayout)        | `layout_`         |
| `CheckBox`                           | `check_`          |
| `CarView`                            | `card_`           |
| `ProgressBar`                        | `progress_`       |

Image view example:

```xml
<ImageView
    android:id="@+id/image_profile"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```

Menu example:

```xml
<menu>
	<item
        android:id="@+id/menu_done"
        android:title="Done" />
</menu>
```

Layout example:

```xml
<FrameLayout
    android:id="@+id/layout_content"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

Some specific views like `AppBarLayout`, `RecyclerView`, `Toolbar`, etc should be converted to id in lowercase underscore: `appbar_layout`, `recycler_view`, `toolbar`,...

### 1.2.6 Strings

String names start with a prefix that identifies the section they belong to. For example `registration_email_hint` or `registration_name_hint`. If a string __doesn't belong__ to any section, then you should follow the rules below:


| Prefix               | Description                                   |
| -----------------    | ----------------------------------------------|
| `error_`             | An error message                              |
| `msg_`               | A regular information message                 |
| `title_`             | A title, i.e. a dialog title                  |
| `action_`            | An action such as "Save" or "Create"          |
| `hint_`              | A hint text or description text in image view |

If the string text is under section it belong to, use two prefixes to identifies what purposes of this text. For example `registration_error_invalid_field`, `registration_action_sign_up`.

### 1.2.7 Styles and Themes

Unless the rest of resources, style names are written in __UpperCamelCase__.


## 1.2 Java language naming
