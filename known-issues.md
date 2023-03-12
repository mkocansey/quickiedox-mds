# Known Issues

Below are a couple of known issues. Will try to knock these issues out one at a time but other developers are encouraged to [fork the QuickieDox repo](https://github.com/mkocansey/quickiedox) and attempt to help fix them. Please don't report these issues on GitHub since they are known :).


### Navigation Items Need A Parent

For now the navigation items have been designed to be stacked underneath a parent item. This makes it impossible to just have top level navigation items that can be clicked on. For example, in the QuickieDox navigation on the left, it would have been great to have an `Overview`{.inline} link above `Getting Started`{.inline}.


### Search Could Be Faster

The current implementation of the site-wide search feature can be improved to return results much faster.

### Algolia Integration

We believe a lot of people who have documentation needs would love to have a way to integrate with Algolia. This will provide a good solution to the faster search problem mentioned above. This is quite some work and hopefully will be built into future versions.

### Protecting Pages

We believe some documentations require users to be logged in first before accessing them. Placeholders have been provided for this but not implemented fully. Since this is a vanilla PHP project and we believe people authenticate their users differently, it is hard to land on a one size fits all solution.