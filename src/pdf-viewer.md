# Setting Up `ngx-extended-pdf-viewer` in Angular 15

This guide outlines the steps required to set up and use the `ngx-extended-pdf-viewer` library in an Angular 15 project.

---

## Prerequisites

Ensure you have the following installed:

- **Angular CLI** (v15)

---

## Steps to Setup

### 1. Create an Angular 15 Project

If you don’t have an Angular 15 project, create one by running:

```bash
npx @angular/cli@15 new my-angular-pdf-viewer
```

---

### 2. Install the Library

Install `ngx-extended-pdf-viewer` and its peer dependencies:

```bash
npm install ngx-extended-pdf-viewer@15 pdfjs-dist @types/pdfjs-dist
```

make sure the version is same as the angular CLI in the pacakage.json file
--- "ngx-extended-pdf-viewer": "^15.2.2",

---

### 3. Import the Module

Open your application’s main module file (`src/app/app.module.ts`) and import the `NgxExtendedPdfViewerModule`:

### 4. Add the PDF Viewer to Your Component

Modify the HTML file of your desired component (e.g., `src/app/app.component.html`) to include the PDF viewer:

```html
<ngx-extended-pdf-viewer [src]="samplePDF" backgroundColor="#ffffff" [height]="'90vh'" [useBrowserLocale]="true" [handTool]="false" [showHandToolButton]="true"> </ngx-extended-pdf-viewer>
```

---

### 5. Define the PDF Source

Update the corresponding TypeScript file (e.g., `src/app/app.component.ts`) to include the `samplePDF` variable:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-root",
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  samplePDF = "https://mozilla.github.io/pdf.js/web/compressed.tracemonkey-pldi-09.pdf";
}
```

---

### 6. Run the Application

Start the Angular development server:

```bash
ng serve
```

Open your browser and navigate to `http://localhost:4200`. You should see the PDF viewer displaying the specified PDF file.

---

## Adding Customization Options in `angular.json`:

In the buid > options > assets you can add up the customized ngx-extendible-pdf-viewer part in it to show the pdf according to the assets.

```typescript
"assets": [
              "src/favicon.ico",
              "src/assets",
              {
                "input": "node_modules/ngx-extended-pdf-viewer/assets/",
                "output": "/assets/",
                "glob": "**/*"
              }
            ],
```

### Edit `tsconfig.json` file:

add this in the compilerOptions object

```json
    "typeRoots": ["node_modules/@types"],
    "types": ["pdfjs-dist"]
```

1. **PDF Not Displaying:**

   - Ensure the URL used in the `samplePDF` variable allows cross-origin requests (CORS).
   - Use a CORS proxy if necessary.

2. **Error: Failed to Fetch:**
   - Verify the PDF URL. Host the PDF locally if needed (e.g., place it in the `src/assets` folder).

### Hosting PDFs Locally

- Place the PDF file in the `src/assets` folder of your project.
- Update the `samplePDF` variable:
  ```typescript
  samplePDF = "/assets/your-pdf-file.pdf";
  ```

---

You're all set! You now have a fully functional PDF viewer integrated into your Angular 15 project.
