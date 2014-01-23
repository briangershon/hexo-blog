---
date: '2007-09-04 05:57:55'
layout: post
slug: captchas-a-spam-prevention-feature-for-your-plone-forms
status: publish
title: 'Captchas: A spam prevention feature for your Plone forms'
wordpress_id: '13'
categories:
- Plone
---

Spam leaves no stone unturned.  How does one protect those Plone web forms that are open for anonymous web users to spam, such as the Plone contact form?

I found a straight-forward and effective solution offered by the [PloneCaptcha](http://sourceforge.net/projects/plonecaptcha/)'s product.  Here are the steps to add this feature to your default Plone contact form.

![Example of PloneCaptchas in action](/images/post/2007/09/plonecaptchas.png)



**Getting Started**

As the product site mentions, you just need a free captchas.net account, and some tweaks to your CMFFormController form template and tweak to your .metadata file to include a new validator.

_PloneCaptchas document errata: The site mentions adding your captchas.net captcha_username and captcha_password to config.py, but you add to PloneCaptcha.py_

**How-To**

For Plone's Contact form, I copied the core templates to my own product's skin folder so they could be customized for adding the captcha:

**contact-info.cpt**

Here I added the field, and included PloneCaptcha's template:

    
    <div class="field"
      tal:define="error errors/captcha|nothing"
      tal:attributes="class python:test(error, 'field error', 'field')">
      <label for="subject">
        Captcha
      </label>
      <span class="fieldRequired" title="Required"
              i18n:attributes="title title_required;"
              i18n:translate="label_required">(Required)</span>
    
      <div class="formHelp">
        To reduce automated spamming, please enter the letters in the box below so we know you're a genuine human.
      </div>
    
      <div tal:content="error">Validation error output</div>            
    
      <div metal:use-macro="here/captcha/macros/edit" />
    </div>


**contact-info.cpt.metadata**

The only change here is in the validators section:

    
    [validators]
    validators=validate_captcha, validate_site_feedback


**validate_site_feedback.vpy**

I also had to tweak this existing form validator so it only returned the customary "please correct the below errors" once -- and not one from the PloneCaptcha validator, and one from mine.  Since I put the captcha validator first in the list, I just checked to see if the state.errors object already has a captcha error, and if yes, it don't send another portal message:

    
    if state.getErrors():
        # don't display two portal messages if the captcha validation fails
        if not state.errors.has_key('captcha'):
            context.plone_utils.addPortalMessage(_(u'Please correct the indicated errors.'))
        return state.set(status='failure')
    else:
        return state
