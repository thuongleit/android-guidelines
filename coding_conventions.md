This guide is super inspired and inherited from [ribot guidelines](https://github.com/ribot/android-guidelines/blob/master/project_and_code_guidelines.md) with a few changes to apply to my projects.

# 1 Coding conventions
## 1.1 Android Resources naming

Resources file names are written in __lowercase_underscore__.

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


## 1.2 Coding Conventions

Need to fully read and understand three official coding conventions below:

* [Code Conventions for the Java TM Programming Language](http://www.oracle.com/technetwork/java/codeconvtoc-136057.html)  - published by Oracle.
* [Code Style for Contributors](http://source.android.com/source/code-style.html) - published by Google.
* [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html) - published by Google.

My Android projects Follow standard Java coding conventions with a few Android specific rules.

## 1.2.1 Fields definition and naming

Fields should be defined at the __top of the file__ and they should follow the naming rules listed below.

* Private, non-static field names start with __m__.
* Private, static field names start with __s__.
* Other fields start with a lower case letter.
* Static final fields (constants) are ALL_CAPS_WITH_UNDERSCORES.

Example:

```java
public class MyClass {
    public static final int SOME_CONSTANT = 42;
    public int publicField;
    private static MyClass sSingleton;
    int mPackagePrivate;
    private int mPrivate;
    protected int mProtected;
}
```

## 1.2.2 Class member ordering

There is no single correct solution for this but using a __logical__ and __consistent__ order will improve code learnability and readability. It is recommendable to use the following order:

1. Constants
2. Fields
3. Constructors
4. Override methods and callbacks (public or private)
5. Public methods
6. Private methods
7. Inner classes or interfaces

Example:

```java
public class MainActivity extends Activity {

	private String mTitle;
    private TextView mTextViewTitle;

    public void setTitle(String title) {
    	mTitle = title;
    }

    @Override
    public void onCreate() {
        ...
    }

    private void setUpView() {
        ...
    }

    static class AnInnerClass {

    }

}
```

If your class is extending an __Android component__ such as an Activity or a Fragment, it is a good practice to order the override methods so that they __match the component's lifecycle__. For example, if you have an Activity that implements `onCreate()`, `onDestroy()`, `onPause()` and `onResume()`, then the correct order is:

```java
public class MainActivity extends Activity {

	//Order matches Activity lifecycle
    @Override
    public void onCreate() {}

    @Override
    public void onResume() {}

    @Override
    public void onPause() {}

    @Override
    public void onDestroy() {}

}
```

## 1.2.3 Parameter ordering in methods

When programming for Android, it is quite common to define methods that take a `Context`. If you are writing a method like this, then the __Context__ must be the __first__ parameter.

The opposite case are __callback__ interfaces that should always be the __last__ parameter.

Examples:

```java
// Context always goes first
public User loadUser(Context context, int userId);

// Callbacks always go last
public void loadUserAsync(Context context, int userId, UserCallback callback);
```

## 1.2.4 String constants, naming, and values

Many elements of the Android SDK such as `SharedPreferences`, `Bundle`, or `Intent` use a key-value pair approach so it's very likely that even for a small app you end up having to write a lot of String constants.

When using one of these components, you __must__ define the keys as a `static final` fields and they should be prefixed as indicated below.

| Element            | Field Name Prefix |
| -----------------  | ----------------- |
| SharedPreferences  | `PREF_`           |
| Bundle             | `ARG_`            |
| Fragment Arguments | `ARG_`            |
| Intent Extra       | `EXTRA_`          |
| Intent Action      | `REQUEST_`        |

Example:

```java
// Note the value of the field is the same as the name to avoid duplication issues
static final String PREF_EMAIL = "PREF_EMAIL";
static final String ARG_AGE = "ARG_AGE";
static final String ARG_USER_ID = "ARG_USER_ID";

static final String EXTRA_SURNAME = "EXTRA_SURNAME";
static final String REQUEST_SIGN_IN = "REQUEST_SIGN_IN";
```

## 1.2.5 Arguments in Fragments and Activities

When data is passed into an `Activity `or `Fragment` via an `Intent` or a `Bundle`, the keys for the different values __must__ follow the rules described in the section above.

When an `Activity` or `Fragment` expects arguments, it should provide a `public static` method that facilitates the creation of the relevant `Intent` or `Fragment`.

In the case of Activities the method is usually called `getStartIntent()`:


```java
public static Intent getStartIntent(Context context, User user) {
	Intent intent = new Intent(context, ThisActivity.class);
	intent.putParcelableExtra(EXTRA_USER, user);
	return intent;
}
```

For Fragments it is named `newInstance()` and handles the creation of the Fragment with the right arguments:


```java
public static UserFragment newInstance(User user) {
	UserFragment fragment = new UserFragment;
	Bundle args = new Bundle();
	args.putParcelable(ARG_USER, user);
	fragment.setArguments(args)
	return fragment;
}
```

__Note 1__: These methods should go at the top of the class before `onCreate()`.

__Note 2__: If we provide the methods described above, the keys for extras and arguments should be `private` because there is not need for them to be exposed outside the class.


# 2 References


* [Ribot Android Guidelines](https://github.com/ribot/android-guidelines)
* [Code Conventions for the Java TM Programming Language](http://www.oracle.com/technetwork/java/codeconvtoc-136057.html)
* [Code Style for Contributors](http://source.android.com/source/code-style.html)
* [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
