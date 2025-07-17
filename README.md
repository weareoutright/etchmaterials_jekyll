# ETCH Materials Website

This project is a static HTML website built with Jekyll and hosted on Siteworx. The local development environment is managed using Jekyll, and deployment to the live server is done via FTP.

## Environments

- **Local**: [http://127.0.0.1:4000/](http://127.0.0.1:4000/)
- **Live**: [https://etchmaterials.com](https://etchmaterials.com)

## Local Development

### Prerequisites

- Ruby 3.1.2 (or compatible version)
- Bundler gem
- Jekyll and related modules as defined in the `Gemfile`

### Setup

1. **Clone the repository:**
    ```sh
    git clone git@github.com:weareoutright/etchmaterials_jekyll.git
    cd etchmaterials_jekyll
    ```

2. **Install dependencies:**
    ```sh
    bundle install
    ```

3. **Start the Jekyll development server:**
    ```sh
    bundle exec jekyll serve
    ```
    
    The site will be available at [http://127.0.0.1:4000/](http://127.0.0.1:4000/)
    
    > **Note**: You must use the Jekyll server to view the site locally. Opening `_site/index.html` directly in a browser won't work due to absolute path references.

4. **Build for production:**
    ```sh
    bundle exec jekyll build
    ```
    
    This generates the static site in the `_site` directory.

### Common Development Commands

- **Serve with auto-reload**: `bundle exec jekyll serve --watch`
- **Build and serve**: `bundle exec jekyll serve --build`
- **Clean build cache**: `bundle exec jekyll clean`

## Deployment

This site automatically deploys to [https://etchmaterials.com](https://etchmaterials.com) using GitHub Actions when changes are pushed to the `main` branch.

### Deployment Workflow

The deployment process uses GitHub Actions to:

1. **Build the Jekyll site** using Ruby 3.1 and bundler
2. **Deploy via FTP** to the Siteworx server
3. **Upload only changed files** for efficient deployments

### Contributing Workflow

#### For Content Updates (News, Team Changes, etc.)

1. **Create a feature branch** from `main`:
   ```sh
   git checkout main
   git pull origin main
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** (add news articles, update team info, etc.)

3. **Test locally**:
   ```sh
   bundle exec jekyll serve
   ```
   Review your changes at [http://127.0.0.1:4000/](http://127.0.0.1:4000/)

4. **Commit and push**:
   ```sh
   git add .
   git commit -m "Description of your changes"
   git push origin feature/your-feature-name
   ```

5. **Create a Pull Request** on GitHub:
   - Go to the repository on GitHub
   - Click "New pull request"
   - Select your feature branch
   - Add a description of your changes
   - Request review from team members

6. **Deploy**: Once the PR is approved and merged into `main`, the site will automatically deploy

#### For Larger Changes (Design, Structure, etc.)

Follow the same workflow as above, but consider:

- Creating a more detailed PR description
- Testing more thoroughly across different pages
- Coordinating with team members before deployment

### Deployment Configuration

The deployment is configured in `.github/workflows/deploy.yml` and requires these GitHub repository secrets:

- `SFTP_SERVER` - The Siteworx server hostname
- `SFTP_USERNAME` - FTP username
- `SFTP_PASSWORD` - FTP password

### Monitoring Deployments

- View deployment status in the "Actions" tab on GitHub
- Failed deployments will show error details in the action logs
- The deployment typically takes 2-3 minutes to complete

### Emergency Rollback

If a deployment causes issues:

1. **Quick fix**: Make a hotfix on a new branch, create PR, and merge
2. **Revert**: Use GitHub's "Revert" button on the problematic commit
3. **Manual deployment**: Contact the repository administrator for manual FTP access if needed

## Content Management

### Adding News Articles

The website supports two types of news articles:

#### 1. Local News Articles (Jekyll Posts)

For company news, press releases, and other content that should be hosted locally:

1. **Create a new file** in the `_posts` directory with the format:
   ```
   YYYY-MM-DD-Title-With-Hyphens.markdown
   ```
   Example: `2025-07-17-ETCH_Names_Ken_Hughes_VP_of_Engineering.markdown`

2. **Add front matter** at the top of the file:
   ```yaml
   ---
   layout: post
   title: "Your Article Title"
   date: 2025-07-17 10:00:00 -0400
   categories: news
   ---
   ```

3. **Write the article content** in Markdown format below the front matter.

4. **Build and test** locally:
   ```sh
   bundle exec jekyll serve
   ```

#### 2. External News Links

For articles published on external websites (media mentions, interviews, etc.):

1. **Edit the file** `_data/external_news.yml`

2. **Add a new entry** to the list:
   ```yaml
   - title: "Article Title"
     url: "https://external-website.com/article-url"
     date: "2025-07-17"
     excerpt: "Brief description of the article content..."
   ```

3. **Build and test** locally to verify the new link appears in the news feed.

#### News Display Behavior

- All news items (local posts and external links) are automatically sorted by date in reverse chronological order
- External links automatically open in a new tab/window (`target="_blank"`)
- Local articles link to the full article page on the website
- The news feed is displayed on `/news/` and automatically updates when new content is added

### Updating Team Information

#### Homepage Team Section

Edit `_layouts/home.html` to modify the team section. Key areas:

- **Leadership section**: Update the `ul.leadership` list for C-level executives
- **Team section**: Update the second `ul` for other team members
- **Images**: Place team photos in `assets/images/` directory

#### Who We Are Page

Edit `who-we-are/index.html` to add or modify detailed team member biographies.

### Managing Images

- Place all images in the `assets/images/` directory
- Use web-optimized formats (PNG, JPG, SVG)
- Reference images in templates using `/assets/images/filename.ext`

## Configuration

The site configuration is managed through `_config.yml`. Key settings include:

* Site title and description
* Base URL configuration
* Build settings and environment variables
* Collections and defaults
* Plugin configurations

Jekyll dependencies are managed using the `Gemfile`.

## Troubleshooting

### Common Issues

**Jekyll server won't start:**
- Ensure Ruby and Bundler are installed
- Run `bundle install` to install dependencies
- Check that you're in the correct directory

**Images not displaying:**
- Verify images are in the `assets/images/` directory
- Check that file paths start with `/assets/images/`
- Ensure image file names match exactly (case-sensitive)

**News articles not appearing:**
- Check that Jekyll posts follow the correct naming convention: `YYYY-MM-DD-title.markdown`
- Verify front matter is properly formatted with `---` delimiters
- For external news, ensure the YAML syntax is correct in `_data/external_news.yml`

**Site looks broken when opening `_site/index.html` directly:**
- Use `bundle exec jekyll serve` instead of opening files directly
- Jekyll uses absolute paths that require a server to resolve correctly

**Build fails:**
- Run `bundle exec jekyll clean` to clear the cache
- Check for syntax errors in Markdown files or YAML front matter
- Verify all required dependencies are installed

### Getting Help

- Check the [Jekyll documentation](https://jekyllrb.com/docs/)
- Review the build output for specific error messages
- Ensure all file paths and names are correct

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.