# Snibox
Snibox selfhosted snippet, an sqlite version for my personal use based on [pivpav](https://gitlab.com/pivpav/snibox-sqlite)
I will try to maintain and develop some new features as I need. Contributions are welcomed from everyone. 

## Changelog
- Added `LaTeX` support
- Added `TOML` support
- Added `Octave`/`Matlab` support
- Added support to `arm` and `arm64` 



## Build
To build this image use following command:

```bash
git clone https://github.com/MohamedElashri/Snibox
docker build -t snibox .
```

To use this image 

`docker pull melashri/snibox:latest`


Or pass the variables directly (port and bind to a local volume)

```bash
docker run -d --name snibox \
              --volume /home/snibox/app/db:/app/db/database \
              --publish 4500:3000 \
              --restart always \
              melashri/snibox
```

Container runs `rake db:migrate` on every start, in order to create database file if not exist, or update database scheme if required, so backups are highly recommended.

### Environment variables

`DATABASE` - Defines sqlite3 database file location within container.

_Default_: `/app/db/database/snibox.sqlite3`

---

`SECRET_KEY_BASE` - Defines `secret_key_base` parameter for your Rails application. Default one is included into the image already, but general recommendation is to change it.

---

`LOGLEVEL` - Defines logging level for Rails application. Available options are: `debug`, `info`, `warn`, `error` and `fatal`

_Default_: `debug`
