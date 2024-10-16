# Anvil Setup and Integration with Python

This README provides step-by-step instructions for setting up and using [Anvil](https://anvil.works/) with Python. Anvil is a platform for building web apps with a drag-and-drop interface, where you can write both client-side and server-side code in Python.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Step 1: Sign Up on Anvil](#step-1-sign-up-on-anvil)
- [Step 2: Create a New App](#step-2-create-a-new-app)
- [Step 3: Set Up the App Design](#step-3-set-up-the-app-design)
- [Step 4: Add Python Code in Anvil](#step-4-add-python-code-in-anvil)
- [Step 5: Install and Use Anvil Uplink](#step-5-install-and-use-anvil-uplink)
- [Step 6: Call Python Functions from Anvil](#step-6-call-python-functions-from-anvil)
- [Step 7: Test and Run Your App](#step-7-test-and-run-your-app)
- [Step 8: Deploy Your App](#step-8-deploy-your-app)
- [Additional Resources](#additional-resources)

## Prerequisites

- Python installed locally (version 3.6 or later).
- An internet connection and a browser to access the [Anvil platform](https://anvil.works/).

## Step 1: Sign Up on Anvil

1. Visit the [Anvil website](https://anvil.works/).
2. Sign up using your email or Google account.
3. Log in to access the Anvil editor.

## Step 2: Create a New App

1. In the Anvil dashboard, click on **New App**.
2. Choose a template (e.g., **Blank App**) to start with.
3. This will open the Anvil editor where you can design your app interface.

## Step 3: Set Up the App Design

1. In the editor, you'll see a variety of UI components (buttons, text boxes, labels, etc.) on the left.
2. Drag and drop components onto the canvas to design your app.
3. Modify the properties of each component (e.g., text, color, size) using the panel on the right.

## Step 4: Add Python Code in Anvil

1. Click on the **Code** tab (located at the bottom of the editor).
2. You'll find Python functions tied to your UI components. For example, if you added a button, you’ll see a function like `button_click`.
3. Write your logic inside the generated functions. Example:
    ```python
    def button_click(self, **event_args):
        self.label_1.text = "Button Clicked!"
    ```

## Step 5: Install and Use Anvil Uplink

Anvil Uplink allows you to connect your local Python environment to your Anvil app.

1. Install the Anvil Uplink package:
    ```bash
    pip install anvil-uplink
    ```
2. In your Python script, connect to your Anvil app using the Uplink key:
    ```python
    import anvil.server

    anvil.server.connect("<Your-Uplink-Key>")
    ```
   > **Note**: You can find the Uplink key in your Anvil app by navigating to the **Uplink** section under "App Dependencies".

3. For more information, check the [Anvil Uplink documentation](https://anvil.works/docs/uplink).

## Step 6: Call Python Functions from Anvil

Once the Uplink is set up, you can call Python functions from Anvil.

1. Define a function in your local Python script that you want to expose to Anvil:
    ```python
    @anvil.server.callable
    def say_hello(name):
        return f"Hello, {name}!"
    ```
2. In the Anvil editor, call this function from the Python code:
    ```python
    def button_click(self, **event_args):
        name = self.text_box_1.text
        greeting = anvil.server.call('say_hello', name)
        self.label_1.text = greeting
    ```

## Step 7: Test and Run Your App

1. Click the **Run** button at the top right of the Anvil editor to test your app.
2. You can interact with your app in the browser to see how it works.

## Step 8: Deploy Your App

1. When you're ready to share your app, click the **Publish** button at the top of the editor.
2. You'll receive a public URL that you can share with others.
   
   Learn more about deploying your app in the [Anvil deployment guide](https://anvil.works/docs/deployment).

## Additional Resources

- **Anvil Docs**: [https://anvil.works/docs/](https://anvil.works/docs/)
- **Anvil Uplink Documentation**: [https://anvil.works/docs/uplink](https://anvil.works/docs/uplink)
- **Python Integration with Anvil**: [Anvil + Python Guide](https://anvil.works/learn/tutorials/python-external)
