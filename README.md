# PHP wrapper for Instamojo API

Assists you to create, edit and delete offers on Instamojo using PHP.

## Usage

### Create a new instance

```php
$instance = new Instamojo('TOKEN_FROM_INSTAMOJO', 'USERNAME', 'PASSWORD');
```

Authenticate the instance by sending the `username` & `password` and in turn receiving a Authentication Token.

```php
$auth = $instance->apiAuth();
```

Creating an offer.
This will give you JSON object containing details of the offer that was just created.

```php
$instance->setTitle('TITLE');
$instance->setDescription('DESCRIPTION');
$instance->setCurrency('INR');
$instance->setBasePrice('100');
$instance->setFilePath('IMG.jpg');
$instance->setCoverPath('COVER.jpg');
$offer = $instance->createOffer();
```

### Using an already existing authentication token

```php
$instance = new Instamojo('TOKEN_FROM_INSTAMOJO');
$instance->setAuthToken('AUTH_TOKEN');
```

## Available Functions

You have these functions to interact with the API:

 * `getVersion()` Get the version of the API wrapper.
 * `setAuthToken()` Set the authentication token for the current instance. This method is used when you have already authenticated the application once for a user and wish to reuse it.
 * `apiAuth()` Authenticate the application.
 * `listAllOffers()` List all the offers of the user.
 * `listOneOfferDetail(slug)` List the complete offer details of the offer id mentioned in slug.
 * `deleteAuthToken()` WARNING!! Deletes the authentication token received from Instamojo. Nothing will work after deleting this.
 * `archiveOffer(slug)` Archives(Deletes) the offer whose id is supplied.
 * `setTitle(title)` Title, keep concise since slug is auto-generated.
 * `setDescription(description)` Detailed description of the offer, can contain markdown.
 * `setCurrency(currency)` Currency of the offer. Can be INR or USD.
 * `setBasePrice(base_price)` Price of the offer as a decimal (up to 2 decimal places)
 * `setQuantity(quantity)` Keep zero for unlimited quantity, any other positive number will limit sales/claims of the offer and make it unavailable afterwards.
 * `setStartDate(start_date)` Required for events, date-time when the event begins. Format: YYYY-MM-DD HH:mm
 * `setEndDate(end_date)` Required for events, date-time when the event ends. Format: YYYY-MM-DD HH:mm
 * `setTimeZone(timezone)` Required for events, date-time when the event begins. Format: YYYY-MM-DD HH:mm
 * `setVenue(venue)` Required for events, location where the event will be held.
 * `setRedirectURL(redirect_url)` You can set this to a thank-you page on your site. Buyers will be redirected here after successful payment.
 * `setNote(note)` A note to be displayed to buyer after successful payment. This will also be sent via email and in the receipt/ticket that is sent as attachment to the email.
 * `setFilePath(file_path)` Path to the file you want to sell.
 * `setCoverPath(cover_path)` Path to the cover image. This resolution of this image should be 950X320.
 * `createOffer()` Function to create an Instamojo offer.
 * `editOffer(slug)` Function to to edit an offer.


For `createOffer()`, `setTitle(title)`, `setBasePrice(base_price)` and `setCurrency(currency)` are the bare minimum
pieces of information that is required. You can (and should) as much relevant information as possible.

