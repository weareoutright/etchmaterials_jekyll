# etchmaterials

This project is a static HTML website, build with Jekyll, and hosted on Siteworx. The local development environment is managed using Jekyll, and deployment to the live server is done via FTP.

## Environments
Local: [http://127.0.0.1:4000/](http://127.0.0.1:4000/)

Live: [https://etchmaterials.com](https://etchmaterials.com)

## Local Development

### Prerequisites

- Ruby 3.1.2
- Jekyl and related modules as defined in the `Gemfile`

### Setup

1. Clone the repository:
    ```sh
    git clone git@github.com:weareoutright/etchmaterials_jekyll.git
    cd etchmaterials_jekyll
    ```

2. Start the Jekyll local site:
    ```sh
    bundle install
    bundle exec jekyll serve
    ```

3. Access the local site:
   Open your browser and navigate to [http://127.0.0.1:4000/](http://127.0.0.1:4000/)

4. Build for production:
    ```sh
    bundle exec jekyll build
    ```

## Deployment

### Prerequisites

* FTP client (e.g., FileZilla, Cyberduck)
* Credentials for the Siteworx server can be found in "Keeper > Clients > ETCH > ETCH FTP (Siteworx)"

### Steps

1. Build the project (if necessary):
    ```sh
    bundle exec jekyll build
    ```
2. Connect to the Siteworx server using your FTP client with the provided credentials.
3. Upload the contents of the `_site` directory to the appropriate directory on the server: "/etchmaterials.com/html"
5. Be CAREFUL, this is a static HTML site and there is an index.html in several different directories. Make sure you don't accidentally transfer the files into the wrong places!
4. View live site at [https://etchmaterials.com](https://etchmaterials.com).

## Configuration

The site configuration is managed through _config.yml. Key settings include:

* Site title and description
* Base URL configuration
* Build settings and environment variables
* Collections and defaults
* Plugin configurations

Jekyll dependencies are managed using the `Gemfile`.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.