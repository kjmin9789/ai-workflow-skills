# Input

A plan produced by `planning-refiner`, condensed to the parts relevant for
writing requirements:

> Goal: Reduce notification opt-out rate by giving users granular control
> over notification categories.
>
> Selected Flow: User opens "Notification Settings" from account settings,
> sees a list of categories (Comments, Likes, Mentions, Marketing) each with
> an on/off toggle, and changes persist immediately. A confirmation toast
> appears after each change; a failed save shows an inline error with retry.
>
> Scope: Per-category toggles, immediate persistence, migration of existing
> users (all categories on by default), new users default Marketing to off.
>
> Out of scope: Notification frequency/scheduling settings, per-device
> settings.
