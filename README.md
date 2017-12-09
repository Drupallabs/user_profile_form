# User Profile Form

## What this module does
This module allows you to separate fields on the user form into two separate forms/tabs, the regular user edit form and a separate "Profile" form. This makes it possible to simplify the standard edit form and even style the 'edit' and 'profile' forms differently.

## Installation and configuration
Install the module as usual. 

- Go to `admin/structure/display-modes/form` and create a new 'Form mode' for the `User` entity type, and call it 'Profile'.
- Edit the form display for the user fields by going to `admin/config/people/accounts/form-display`.
- Scroll down to the bottom of the page and open the collapsed fieldset labeled `Custom Display Settings`.
- You'll see a checkbox for 'Profile'. Check it and save the change.
- Scroll back up to the top of the page and you'll see two tabs, one calle 'Default' and another called 'Profile'. 
- Set each of them up with the fields that should be displayed on each form, and save the results.
- Go to any user account page. You should see an `Edit` tab that has the `Default` fields, and a `Profile` tab that has the `Profile` fields.

Drupal core already provides another form mode called `Register`. You can also enable that form on the `Manage form display` page to identify and limit the specific fields you want to see on the form a user sees during the registration process. 

For instance, you might want to change the default behavior of asking for a user picture during registration by removing that field from the `Register` and `Edit` forms, and displaying that field on the `Profile` form instead.

## Altering the form

If you want to make other changes to the profile, use something like the following:

```
use \Drupal\Core\Form\FormStateInterface;

/**
 * Implements hook_form_BASE_FORM_ID_alter().
 */
function user_profile_form_form_user_form_alter(&$form, FormStateInterface $form_state, $form_id) {

  switch ($form_id) {

    // The primary edit form.
    case 'user_form':
      break;

    // The user registration form.
    case 'user_register_form':
      break;

    // The profile edit form.
    case 'user_profile_form':
      break;

  }
}
```
## Resources and Credits

Ideas for this module came partly from the following:

 * [https://www.webomelette.com/render-custom-entity-form-modes-programatically-drupal-8](https://www.webomelette.com/render-custom-entity-form-modes-programatically-drupal-8)
 * [https://www.drupal.org/docs/8/api/entity-api/display-modes-view-modes-and-form-modes](https://www.drupal.org/docs/8/api/entity-api/display-modes-view-modes-and-form-modes)
 * [https://www.drupal.org/docs/8/api/routing-system/structure-of-routes](https://www.drupal.org/docs/8/api/routing-system/structure-of-routes)

 