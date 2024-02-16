## Abstract

This branch experiments with integrating Decap (previously Netlify CMS) into HydePHP.

### Design & Implementation

There are a few ways we can ship the integration:
- A command that scaffolds the configuration files that are needed
  - The command can then prompt for things like GitHub repo and deployment URL
- An extension to the Realtime Compiler which serves the files needed, and can inject environment variables
- A separate Composer plugin

Currently the implementation is through a decoupled `_admin/` directory with a custom PHP server to handle dynamic injections. This can then later be adapted to the desired bundling option.

Since the CMS connects to GitHub, we could even add an option to add the static admin panel HTML and its generated config to the built site, as authentication is handled by GitHub.

We could even experiment with having a hosted version at cms.hydephp.com where users can connect any repo and we can proxy the files from there.

### Background and Stack

The resulting integration is very lightweight, as the React application is loaded from a CDN. We only need to provide the configuration data and base HTML page.

### Benefits

The main benefit of us providing this, compared to for example the user setting up their own headless CMS (Decap or otherwise), is that we our configuration file is already implemented for HydePHP sites, drastically reducing the friction.

Hopefully, something like this will make it easier for agencies and freelancers to create websites with HydePHP for their clients, who can then later update content by themselves.

---

## Testing

The integration proof of concept can be started with the following command:

```bash
php -S localhost:3000 _admin/index.php
```

## Issues

At the moment, it seems to be hard to get support for Blade pages.

## Resources

See https://github.com/hydephp/develop/pull/1571
