# Tailwind CSS v4 Installation Guide for Django

This guide will walk you through the steps to install and configure Tailwind CSS v4 in your Django project.

## Prerequisites

- Node.js and npm installed
- Django project set up

## Installation Steps

### 1. Install Required Packages

```bash
npm install tailwindcss @tailwindcss/postcss postcss
```

### 2. Create PostCSS Configuration

Create a file named `postcss.config.mjs` in your project's root directory with the following content:

```javascript
export default {
  plugins: {
    "@tailwindcss/postcss": {},
  },
};
```

### 3. Create Input CSS File

Add the following code in `static/css/input.css`:

```css
@import "tailwindcss";
```

### 4. Configure Package.json

Add the following scripts to your `package.json` file:

```json
"scripts": {
  "build:tailwind": "npx @tailwindcss/cli -i ./static/css/input.css -o ./static/css/output.css --minify",
  "watch:tailwind": "npx @tailwindcss/cli -i ./static/css/input.css -o ./static/css/output.css --watch"
}
```

### 5. Include Tailwind CSS in Your Templates

Add the following code to the HTML files where you want to use Tailwind CSS:

```html
{% load static %}
<!-- Add this at the top of your HTML file -->

<link rel="stylesheet" href="{% static 'css/output.css' %}" />
```

> **Note:** Make sure to add `{% load static %}` at the top of your HTML file.

### 6. Start the Tailwind CSS Build Process

Open a terminal and run the following command to start the Tailwind CSS build process in watch mode:

```bash
npm run watch:tailwind
```

For production, use:

```bash
npm run build:tailwind
```

## Usage

You can now use Tailwind CSS classes in your Django templates. For example:

```html
<div class="bg-blue-500 text-white p-4 rounded-lg shadow-md">
  Hello, Tailwind CSS!
</div>
```

## Additional Resources

- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Django Documentation](https://docs.djangoproject.com/)
