Django version
--------------

To use the django package, add it to your app using:

    pip install moj_template

Then extend your base template from the moj_template using:

    {% extends 'moj_template/base.html' %}

Config
------

You will be required to set up some additional config to use the package. Add the following to your `TEMPLATE_CONTEXT_PROCESSORS`:

    "{app_path}.apps.core.context_processors.globals"

Then include the following in a new file called `apps/core/context_processors.py`:

    def globals(request):
      return {
        'app_title': '', # Application Title (Populates <title>)
        'proposition_title': '', # Proposition Title (Populates proposition header)
        'phase': '', # Current Phase (Sets the current phase and the colour of phase tags). Presumed values: alpha, beta, live
        'product_type': '', # Product Type (Adds class to body based on service type). Presumed values: information, service
        'feedback_url': '', # Feedback URL (URL for feedback link in phase banner)
        'ga_id': '', # Google Analytics ID (Tracking ID for the service)
        'html_lang': 'en', # `lang` attribute for the <html> element
        'skip_link_message': 'Skip to main content', # Contents of the 'skip to main content' link
        'logo_link_title': 'Go to the GOV.UK homepage', # Contents of the `alt` attribute for the main logo
        'crown_copyright_message': '&copy; Crown copyright' # Contents of the copyright message below the crown logo in the footer
      }