# 🧪 TBC Digital Automation Framework — Final Project 2

## 🎯 Objective
Develop a robust and scalable automation framework for TBC Digital with comprehensive test coverage, including functional testing, visual regression testing, and data-driven test execution using modern tools and best practices.

---

## 🔧 Tech Stack

| Tool | Purpose |
|------|-------------------------------------------------|
| **Java** | Core programming language |
| **Playwright** | Browser automation |
| **TestNG** | Test execution framework (parallel support) |
| **JDBC** | Local SQL database for test data parametrization |
| **TestNG DataProvider** | Data-driven test execution |
| **BackstopJS** | Visual regression testing |
| **Maven** | Build & dependency management |

---

## 📋 Prerequisites

- **JDK 17+**
- **Maven 3.8+**
- **Node.js 16+** (for BackstopJS)
- **SQL Server**
- browsers: Chrome, Firefox, Safari/WebKit

---

## 📁 Project Structure

```
src/
├── main/java/
│ ├── pages/ # Page Objects (selectors only)
│ ├── steps/ # Actions + assertions
│ ├── utils/ # Helper utilities
│ └── data/ # Constants, configurations
├── resources/
│ └── database.properties # Database setup
├── test/java/
│ ├── tests/ # Test classes (Desktop & Mobile)
│ └── runners/ # BaseTest, driver setup
├── testng.xml # Both Suites configuration
├── testngDesktop.xml # Desktop configuration
├── testngMobile.xml # Mobile configuration
├── backstop_data/
│ └── engine_scripts/ # BackstopJS automation scripts
└── backstop.json # BackstopJS main configuration
```

---

## 🗄️ Database Schema

### Location Test Cases
```sql
CREATE TABLE location_cases (
id INT,
area VARCHAR(100),
expected_min_results INT
);

INSERT INTO location_cases VALUES
(1, 'Vazisubani', 2),
(2, 'Varketili', 8),
(3, 'Vake', 25);
```

### Address Test Cases
```sql
CREATE TABLE address_cases (
id INT,
address VARCHAR(100),
expected_location_addresses NVARCHAR(500)
);

INSERT INTO address_cases (id, address, expected_location_addresses) VALUES
(1, 'Tevdore Mgvdeli', N'#13 Tevdore Mgvdeli Str.,#29 Tevdore Mgvdeli Str.,#44a Tevdore Mgvdeli'),
(2, 'petefi', N'#7 Petefi Str.'),
(3, 'dolidze', N'#7 Dolidze Str.,#11 Dolidze Str.');
```

### City Test Cases
```sql
CREATE TABLE city_cases (
id INT,
city VARCHAR(50),
expected_address NVARCHAR(500)
);

INSERT INTO city_cases (id, city, expected_address) VALUES
(1, 'Abastumani', N'#41 Asatiani Str.'),
(2, 'Anaklia', N'Anaklia Vlg.'),
(3, 'ASPINDZA', N'#33 Vardzia Str.,#3 Tamari Str.');
```

---

## ⚙️ Environment Configuration

- **Base URL**: Stored in `Constants.TBC_BASE_URL`
- **Viewport Configuration**: Desktop (1920x1080) and Mobile (375x812)
- **Browser Support**: Chrome, Firefox, WebKit
- **Parallel Execution**: Configured via `testng.xml`
- **Geolocation**: Pre-configured for Tbilisi coordinates (41.698, 44.800)

---

## 🚀 How to Run

### 1. Functional Tests
run from testng.xml
### 2. Visual Regression Tests

**Create baseline screenshots:**
```bash
npx backstop reference # create baseline
```

**Run visual comparison:**
```bash
npx backstop test # compare
```

---

## 🔄 Parallel Execution

Tests run in parallel with the following configuration:
- **Thread Count**: 8 (configurable in `testng.xml`)
- **Parallel Level**: `classes` - each test class runs in its own thread
- **Browser Instances**: Each thread gets its own browser instance
- **Cross-Browser**: Supports parallel execution across different browsers

---

## 📱 Desktop vs Mobile Testing

Tests are designed to work on both desktop and mobile viewports:
- **Shared Test Logic**: Same test methods for both viewports
- **Conditional Steps**: Platform-specific actions handled via `if-else` statements
- **Responsive Selectors**: Different locators for mobile vs desktop when needed

---

## 🎯 Test Coverage

### Functional Test Scenarios (8 total)
1. **Product Details Test** - Pupil Card navigation and validation
2. **ATM Availability Test** - Location filtering and 24/7 availability
3. **Branches Search** - Address-based branch finding
4. **City-Based Filtering** - Location search by city
5. **Offers Filtering** - Product offers with multiple criteria
6. **Map Integration** - Startup location validation
7. **Mobile Navigation** - Mobile-specific user flows
8. **Branches Availability Test** - Location filtering and 24/7 availability

### Data-Driven Tests
- **SQL Database Parametrization**: Location search scenarios
- **TestNG DataProvider**: Offers filtering combinations

### Visual Regression
- **ATM Page Comparison**: Before/after filter application
- **Cross-Browser Screenshots**: Visual consistency across browsers

---

## 🛠️ Key Features

- ✅ **Multi-Browser Support**: Chrome, Firefox, WebKit
- ✅ **Mobile Emulation**: iPhone viewport simulation
- ✅ **Database Integration**: SQL Server with JDBC
- ✅ **Visual Testing**: BackstopJS integration
- ✅ **Parallel Execution**: TestNG parallel configuration
- ✅ **Page Object Model**: Clean separation of concerns
- ✅ **Fluent API**: Chainable step methods

---

## 🏆 Project Achievements

This framework successfully implements all requirements from the Final Project 2 specification:

- **Playwright Migration** ✅ Complete rewrite from Selenide
- **Multi-Browser Execution** ✅ Chrome, Firefox, WebKit support
- **SQL Database Integration** ✅ Location test parametrization
- **TestNG DataProvider** ✅ Offers test scenarios
- **Visual Regression Testing** ✅ BackstopJS implementation
- **Mobile + Parallel Execution** ✅ Full TestNG configuration

---