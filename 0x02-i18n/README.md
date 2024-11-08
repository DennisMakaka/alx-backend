# i18n with Flask and Flask-Babel

## Project Overview
This project focuses on localizing a Flask web application, providing language translation capabilities based on user preferences or request data. Key objectives include locale and timezone management, template parameterization for translations, and using Flask-Babel for user-specific language support.

## Task Breakdown

### Task 0: Basic Flask App Setup
- **Goal**: Create a minimal Flask app (`0-app.py`) with a root route (`/`) that renders a template (`0-index.html`).
- **Details**:
  - Set the `<title>` tag in `index.html` to "Welcome to Holberton".
  - Add a `<h1>` tag with "Hello world".

### Task 1: Basic Babel Setup
- **Goal**: Install Flask-Babel, configure it, and set up a base language configuration.
- **Steps**:
  - Install Flask-Babel.
  - Define a `Config` class with `LANGUAGES` as `["en", "fr"]`, default locale as `"en"`, and default timezone as `"UTC"`.
  - Apply the config to the Flask app’s configuration.

### Task 2: Locale Determination from Requests
- **Goal**: Define a `get_locale` function using the `babel.localeselector` decorator to detect the best match for languages based on the `Accept-Language` request header.
- **Details**: Use `request.accept_languages` to identify the best language match from the supported languages specified in `Config.LANGUAGES`.

### Task 3: Template Parameterization and Translations
- **Goal**: Enable translation keys in templates using Babel.
- **Steps**:
  - Use `_` or `gettext` in your templates for dynamic text (e.g., replace static text with keys like `home_title` and `home_header`).
  - Create a `babel.cfg` file to specify extraction rules for `.py` and `.html` files.
  - Run extraction and initialize message catalogs.

### Task 4: Locale Parameter in URL
- **Goal**: Allow locale specification via a URL parameter (`?locale=fr`).
- **Steps**:
  - Modify `get_locale` to prioritize the locale parameter in the URL query string.

### Task 5: Mocking User Login
- **Goal**: Emulate user login with a `login_as` parameter to fetch user data.
- **Details**:
  - Create a user mock dictionary to simulate a database.
  - Define `get_user` to retrieve user info based on the login ID.
  - Add a `before_request` function to set `flask.g.user` to the current user if any.
  - Update the HTML template to display a welcome message if logged in or a default message if not.

### Task 6: Locale Selection Based on User Preferences
- **Goal**: Update `get_locale` to consider a user’s preferred locale if available.
- **Priority Order**:
  1. Locale from URL parameters.
  2. Locale from user settings in `get_user`.
  3. Locale from request header.
  4. Default locale.

### Task 7: Inferring Timezone
- **Goal**: Define a `get_timezone` function with the `babel.timezoneselector` decorator to determine timezone.
- **Details**:
  - Priority: URL parameter timezone, user’s preferred timezone, default to UTC.
  - Validate timezone input as needed.

### Advanced Task 8: Displaying Current Time
- **Goal**: Display the current time on the home page based on inferred timezone, in both English and French.
- **Translation Keys**:
  - English: "The current time is %(current_time)s."
  - French: "Nous sommes le %(current_time)s."

## Key Files
- **app.py**: Main Flask application file for each task.
- **index.html**: HTML templates with translated text.
- **babel.cfg**: Babel configuration file for extraction.
- **translations/**: Directory for language files (.po, .mo files) for each language (en, fr).
