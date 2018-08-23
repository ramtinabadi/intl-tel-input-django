# intl-tel-input-django
How to add intl-tel-input jQuery plugin into Django.

Django comes with a series of form widgets which you add into your `forms.py`.
However, while using intl-tel-input, which gives a beautiful dropdown for mobile number, you will face a problem adding the `tel` input type to the form. You can get the files and read the documentations of intl-tel-input [here](https://github.com/jackocnr/intl-tel-input)

In order to use the plugin in Django, you have to create a simple custom widget and use it in your field. You can user the following:

```
    from django.forms.widgets import Input
    
    class TelInput(Input):
        input_type = 'tel'
    
    class SampleForm(forms.Form):
        phone = forms.CharField(
            widget=TelInput(
                attrs={
                    'placeholder': '',
                    'autocomplete': 'off'
                }
            ),
            required=False,
        )
```       

In the template, just like any other form, you render the field. To initialise the intl-tel-input on the field, you have to do these steps:

1. Import the css file in `head`

```
    <link rel="stylesheet" href="{% static 'build/css/intlTelInput.css' %}">
 ```   
   
2. Import the `intlTelInput.js` and `utils.js` in the `body`

```
    <script src="{% static 'build/js/intlTelInput.js' %}"></script>
    <script src="{% static 'build/js/utils.js' %}"></script>
   ``` 

3. render the form field wherever and however you want

4. Initialise the field
```
    <script type="text/javascript">
        $("#id_phone").intlTelInput();
    </script>
```
    
The rest is similar to the standard intl-tel-input
