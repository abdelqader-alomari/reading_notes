# Read: 31 - Espresso

## Espresso

Espresso used to write concise, beautiful, and reliable Android UI tests.

![Espresso](https://spin.atomicobject.com/wp-content/uploads/20170925145122/Android-Espresso.png)

### Example

```
@Test
public void greeterSaysHello() {
    onView(withId(R.id.name_field)).perform(typeText("Steve")); \\ check the text
    onView(withId(R.id.greet_button)).perform(click()); \\ check the button
    onView(withText("Hello Steve!")).check(matches(isDisplayed())); \\ check if the text display on the screen
}
```

Espresso tests state expectations, interactions, and assertions clearly without the distraction of boilerplate content, custom infrastructure, or messy implementation details getting in the way.Espresso tests run optimally fast!

### Synchronization capabilities

Each time your test invokes onView(), Espresso waits to perform the corresponding UI action or assertion until:

- The message queue is empty.
- There are no instances of AsyncTask currently executing a task.
- All developer-defined idling resources are idle.

### Sample Test (changeText for new Activity)

```
  @Test
  public void changeText_newActivity() {
    // Type text and then press the button.
    onView(withId(R.id.editTextUserInput)).perform(typeText(STRING_TO_BE_TYPED),
        closeSoftKeyboard());
    onView(withId(R.id.activityChangeTextBtn)).perform(click());
    // support launching a new Activity, so use Espresso Intents to verify intent was sent
    assertThat(Iterables.getOnlyElement(Intents.getIntents())).hasComponentClass(
        ShowTextActivity.class);
  }
```

---

## Create UI tests with Espresso Test

![record espresso](https://i.ytimg.com/vi/v3TOmUlnVbE/maxresdefault.jpg)

The Espresso Test Recorder tool lets you create UI tests for your app without writing any test code.
Espresso Test Recorder then takes the saved recording and automatically generates a corresponding UI test that you can run to test your app.

### Record an Espresso test

Espresso tests consist of two primary components: UI interactions(clicking button / writing note) and assertions(verify the existence of button and content of note) on View elements. UI interactions include tap and type actions that a person may use to interact with your app. Assertions verify the existence or contents of visual elements on the screen

### Record UI interactions

1. Click Run > Record Espresso Test.
2. In the Select Deployment Target window, choose the device on which you want to record the test. Click OK.
3. Interact with your device to start logging events such as "tap" and "type" actions.

Recorded interactions will appear in the main panel in the Record Your Test window, as shown in figure 1 below. When you run the test, the Espresso test will try executing these actions in the same order.

![example](https://developer.android.com/studio/images/test/espresso-test-recorder-window_2-2_2x.png)

### Add assertions to verify UI elements

Assertions verify the existence or contents of a View element through three main types:

- text is: Checks the text content of the selected View element
- exists: Checks that the View element is present in the current View hierarchy visible on the screen
- does not exist: Checks that the View element is not present in the current View hierarchy

To add an assertion to your test, proceed as follows:

- Click Add Assertion. A Screen Capture dialog appears while Espresso gets the UI hierarchy and other information about the current app state. The dialog closes automatically once Espresso has captured the screenshot.
- A layout of the current screen appears in a panel on the right of the Record Your Test window. To select a View element on which to create an assertion, click on the element in the screenshot or use the first drop-down menu in the Edit assertion box at the bottom of the window. The selected View object is highlighted in a red box.
- Select the assertion you want to use from the second drop-down menu in the Edit assertion box. Espresso populates the menu with valid assertions for the selected View element.
- If you choose the "text is" assertion, Espresso automatically inserts the text currently inside the selected View element. You can edit the text to match your desired assertion using the text field in the Edit assertion box.
  Click Save and Add Another to create another assertion or click Save Assertion to close the assertion panels.

The screenshot in figure 2 shows a "text is" assertion being created to verify that the title of the note is "Happy Testing!": ![Happy Testing](https://developer.android.com/studio/images/test/espresso-test-recorder-assertion_2-2_2x.png)

### Save Recording

- Click Complete Recording. The **Pick a test** class name for your test window appears.
- Espresso Test Recorder gives your test a unique name within its package based on the name of the launched activity. Use the **Test class name text field** if you want to change the suggested name. Click Save.
- If you have not added the Espresso dependencies to your app, a Missing Espresso dependencies dialog appears when you try to save your test. Click Yes to automatically add the dependencies to your `build.gradle` file.
- The file automatically opens after Espresso Test Recorder generates it, and Android Studio shows the test class as selected in the Project window of the IDE.
- Where the test saves depends on the location of your instrumentation test root, as well as the package name of the launched activity.

---

## References

- [Espresso Testing](https://developer.android.com/training/testing/espresso)
- [Ridiculous superpower: the Espresso Test Recorder](https://developer.android.com/studio/test/espresso-test-recorder)
