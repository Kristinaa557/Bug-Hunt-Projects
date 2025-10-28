# Flowwow.com Testing Project

This project contains bug reports and testing artifacts for the [Flowwow.com](https://flowwow.com/) website.

## Scope
*   **Test Type:** Exploratory Testing (Ad-hoc), Functional Testing, UI/UX Testing
*   **Focus Area:** Main Page, Search, User Registration, Shopping Cart, UI Consistency
*   **Testing Period:** October 2024

## Test Environment
*   **OS:** Windows 11
*   **Browser:** Chrome 119.0.6045.200 (Official Build) (64-bit)
*   **Screen Resolution:** 1920x1080

## Found Issues
| ID | Title | Severity | Priority | Status |
|----|-------|----------|----------|--------|
| `FLO-001` | Поиск не обрабатывает ввод в английской раскладке | Minor | Medium | Open |
| `FLO-002` | Эффект наведения на кнопку "Добавить товары" практически незаметен | Minor | Low | Open |
| `FLO-003` | Невозможно дать согласие на рекламные рассылки при регистрации из-за автоматического закрытия формы | Major | High | Open |

## Project Structure
Project_Flowwow/
├── README.md
├── bug_reports/
│ ├── FLO-001_search_does_not_handle_english_layout.md
│ ├── FLO-002_button_hover_effect_not_visible.md
│ └── FLO-003_form_auto_close_on_checkbox.md
├── test_cases/
│ ├── TC-001_user_registration.md
│ ├── TC-002_search_functionality.md
│ └── TC-003_shopping_cart.md
├── checklists/
│ ├── smoke_checklist_web.md
│ └── regression_checklist_v1.md
└── api_testing/
└── api_checklist.md

## Key Findings
- Discovered 3 reproducible bugs with different severity levels
- Created comprehensive test documentation covering main user flows  
- Prepared API testing checklist for backend verification
- Documented both functional and UI/UX issues
