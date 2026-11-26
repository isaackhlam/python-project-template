install:
		- git submodule update --init --recursive --remote --force
	{% if cookiecutter.environment_manager == "uv" %}
		uv sync --no-dev
	{% elif cookiecutter.environment_manager == "conda" %}
		conda env update -f environment.yml
	{% endif %}

install-dev:
		- git submodule update --init --recursive --remote --force
	{% if cookiecutter.environment_manager == "uv" %}
	uv sync
	uv run pre-commit install
	{% elif cookiecutter.environment_manager == "conda" %}
		conda env update -f environment-dev.yml
		pre-commit install
	{% endif %}

reset:
	git fetch
	git remote prune origin
	git checkout main -f
	git reset --hard origin/main
	git checkout dev -f
	git reset --hard origin/dev
	$(MAKE) install
