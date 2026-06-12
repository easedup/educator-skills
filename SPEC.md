# Educator Skills Search & Download Page - Specification

## 1. Overview
A static web interface for teachers to discover, search, and download agent skills. The page will be generated from the markdown source files in the repository and hosted via GitHub Pages.

## 2. Metadata & Search Robustness
To improve search accuracy and filtering, each `SKILL.md` file will eventually include expanded front matter:
- **`tags`**: A list of keywords (e.g., `formative`, `rubric`, `inclusive`) to improve search matches beyond the name and description. (Note: To be added during the next revision of skill files).
- **`category`**: Inherited from the folder structure but explicitly defined for the UI.

## 3. Recommendation & Rating System
While the skills themselves do not yet contain rating data, the search page will support a recommendation system:
- **Star Rating Indicator**: Visual display of the "recommendation level" for each skill.
- **Data Source**: For this phase, ratings and featured status will be managed via a central metadata configuration file (`metadata.json`) rather than directly in the `SKILL.md` files. This allows for easier curation without touching the core skill source code.

## 4. Filtering & Search Methods
- **Global Search Bar**: Real-time filtering across skill names, descriptions, and tags.
- **Category Navigation**: Quick-filters for pedagogical areas (Assessment, Planning, etc.).
- **Star Rating Indicator**: Visual display of the "recommendation level" (1-5 stars).

## 5. Search Results & UI Components
### Skill Cards
Each skill is represented by a card containing:
- **Header**: Skill name and Category badge.
- **Rating**: A visual star system (1 to 5 stars) indicating the recommendation level.
- **Description**: Truncated summary of the skill's purpose.
- **Actions**:
    - **Download ZIP**: Immediate download of the specific skill folder.
    - **Add to Pack**: Adds the skill to a temporary "collection" for bulk download.

### "My Pack" Sidebar/Bar
- Tracks skills the user has selected.
- **Download Pack**: Generates a single ZIP file containing all selected skill folders.

## 6. Recommendation System (The "Top 3")
Displayed at the top of the page when no search is active:
1. **The Flagship (Most Recommended)**: The item with the highest star rating (e.g., 5 stars).
2. **The Alternative**: A high-value skill (e.g., 4 stars) that addresses a different area of the teaching workflow.
3. **The Newcomer**: The skill with the most recent `released` date or highest version in a new category.

## 7. Technical Implementation
- **Build Engine (`build.js`)**:
    - Scans `skills/` directory.
    - Parses YAML front matter from `SKILL.md`.
    - Generates `public/skills.json` for the frontend.
    - Packages individual skill folders into `.zip` files in `public/downloads/`.
- **Frontend**:
    - Vanilla JS / Tailwind CSS (CDN).
    - Client-side filtering and "Pack" management.
    - (Optional) JSZip for on-the-fly generation of the "My Pack" bulk ZIP.

## 8. Deployment
- Hosted on **GitHub Pages**.
- Automated via GitHub Actions (optional) or manual build script execution.
