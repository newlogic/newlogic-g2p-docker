# openG2P-ng Docker setup

This is a flexible and **streamlined** version to run the project.


## Quick start

You need to have Docker and docker-compose installed.

```bash
$ git clone git@github.com:newlogic/openg2p-docker.git
$ cd openg2p-docker
$ git submodule init
$ git submodule update
$ docker-compose -f docker-compose.yml  -f dev-standalone.yml up
```

Then open http://localhost:8069/


## Known issue

If you are using MacOs with and M1 CPU, you will need to rebuild the docker image first:

```bash
$ docker build -t newlogic42/dockerdoo:15.0 --no-cache .
```


### Project Structure

```bash
your-project/
 ├── resources/         # Scripts for service automation
 ├── src/
 │   └── odoo/          # Just required if using hosted source code
 │
 ├── config/
 │   └── odoo.conf      # Hosted configuration file for hosted environment
 ├── custom/            # Custom modules goes here, same level hierarchy **REQUIRED**
 │   ├── iterativo/
 │   ├── OCA/
 │   ├── enterprise/
 │   └── /
 ├── ...                # Common files (.gitignore, etc.)
 ├── .env               # Single source of environment definition
 ├── Dockerfile         # Single source of image definition
 ├── docker-compose.yml             # The opionated version
 └── docker-compose.override.yml    # Your custom version
```

### Extra addons

You can put all your **custom addons** in the folder `./custom/`, those will be automatically added to your `addons_path` thanks to the script in `./resources/getaddons.py`

## Credits

Mainly based on [dockerdoo](https://github.com/iterativo-git/dockerdoo)
