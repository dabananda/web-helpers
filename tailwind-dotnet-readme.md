# Tailwind CSS Installation Guide for ASP.NET Core

## Prerequisites
- .NET 8 SDK
- Node.js installed

## Step-by-Step Installation Guide

### 1. Create New .NET 8 MVC Project
```bash
dotnet new mvc -n YourProjectName
cd YourProjectName
```

### 2. Initialize npm Project
```bash
npm init -y
```

### 3. Install Tailwind CSS and Dependencies
```bash
npm install -D tailwindcss@3 postcss autoprefixer
```

### 4. Prepare Tailwind CSS Configuration

#### 4.1 Create Tailwind CSS Entry File
Navigate to `wwwroot/css/site.css` and add:
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

#### 4.2 Update package.json Scripts
Add the following scripts to `package.json`:
```json
"scripts": {
    "build:css": "npx tailwindcss -i ./wwwroot/css/site.css -o ./wwwroot/css/output.css --minify",
    "watch:css": "npx tailwindcss -i ./wwwroot/css/site.css -o ./wwwroot/css/output.css --watch"
}
```

#### 4.3 Initialize Tailwind Configuration
```bash
npx tailwindcss init
```

### 5. Configure Tailwind Content Paths
Edit `tailwind.config.js` to include your views:
```javascript
module.exports = {
  content: [
    './Pages/**/*.cshtml',
    './Views/**/*.cshtml',
    './Views/Shared/**/*.cshtml'
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### 6. Add Build Target to Project File
Open your `.csproj` file and add inside the `<Project>` tag:
```xml
<Target Name="BuildCss" BeforeTargets="Compile">
    <Exec Command="npx tailwindcss -i  ./wwwroot/css/site.css -o ./wwwroot/css/output.css --watch" />
</Target>
```

### 7. Install Dependencies and Run
```bash
npm install
npm run watch:css
```

## Usage
- The generated `output.css` will be in `wwwroot/css/`
- Link the `output.css` in your layout file

## Scripts
- `npm run build:css`: Create minified CSS for production
- `npm run watch:css`: Watch and rebuild CSS during development

## Troubleshooting
- Ensure Node.js and npm are correctly installed
- Verify all paths in configuration files
- Check that Tailwind classes are being recognized in your views

## Contributing
Feel free to open issues or submit pull requests to improve this setup.

## License
This project is open-source. Include your specific license information here.
