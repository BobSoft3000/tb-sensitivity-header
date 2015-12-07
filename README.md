# Thunderbird Sensity Header Addon

This simple addon currently allows the user to add a sensitivity indicator ('Personal/Private/Company-Confidential') to an outgoing message via an option in the tools menu, or from an optional drop-down toolbar menu (similar to message priority).
While adding this header does not directly add any security to the message, the header can be interpreted by some MTA/MUAs such that the message is treated differently while in transit, or when viewed by the recipient:
* e.g. MS Outlook/Exchange: Can be set so that confidential/personal messages are unable to be read by the recipient's delegated users; A warning can be displayed before the message is forwareded; Displays an advisory message above content.
* e.g. Some versions of Symantec PGP in corporate set-ups can automatically encrypt the outgoing message if leaving the corporate network, or redirect it to a secure corporate webmail page (with an automated notification email to the recipient to collect it there).

Please note that other MTA/MUA software (e.g. Popular webmail systems, Thunderbird without this add-on) may <i>completely ignore</i> the header as it is not commonly used outside of corporate environments.  Therefore, please do not solely rely on it for ensuring your message is treated as intended.

## Known Issues

* When re-opening a draft message where a sensitivity was set, the previous value is not currently retained.
* Similarly, when forwarding or replying to a message, the sensitivity value from the original message is not currently retained.
As such, please make sure to select the correct sensitivity before sending your messages - if you add the toolbar item, this is always visible when composing.  I hope to find a fix for these issues in a future version.
* This addon does not currently show an indicator for received messages yet - In future versions of this addon, I may add some kind of (optional) banner above the message when the header is set to Personal/Private/Confidential.  In the meantime, if the header has been set on any message, it will be visible if 'View Menu -> Headers -> All' is ticked.

If you're familiar with Thunderbird addon development or can help with translations, and would like to help out, please get in touch.

## Development Plan
* When editing a draft, or replying to a message with this header, make the header in the new message the same.
* Add the toolbar item automatically on install.
* Display an (optional) banner above received message (if header is set to priv/pers/conf).
* Automatically *add* the header to the searchable headers list. (and remove it on uninstall).
 user_pref("mailnews.customHeaders", "Sensitivity");  
 Must **ADD** it to list of searchable message fields in case there are other fields there from other addons  
* Keep UI strings localised where possible.
* When the selected sensitivity is 'normal' when composing, remove the custom header completely.
