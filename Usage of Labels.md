# Usage of Labels

It's easy to get lost in the sea of tickets in GitLab so using labels well is vital. We use both prefixes and colours to 
help organise our labels; pefixes indicate labels that relate to the same topic and colours group labels by a broad theme.

Labels should only be applied to tickets, and not merge requests.

## Prefixes

* `status::` is used to indicate where in the workflow the ticket is. A ticket can only have one of these labels.
* `type::` is used to indicate the type of ticket (eg, bug, feature, question, etc). A ticket can only have one of these 
  labels.
* `area/` is used to indicate which "area" of the website is affected. A ticket can have as many of these as necessary.
* `platform/` is used to indicate which aspect (front or back end) of the site is affected. A ticket can have as many 
  of these as necessary.

> We make use of [GitLab's scoped labels][scoped-labels] (the `::` between the prefix and name) to enforce using only 1 
> of that type of label. For the others, we use a `/` between the prefix and name.

## Colours

TBC

[scoped-labels]: https://gitlab.com/help/user/project/labels.md#scoped-labels-premium
