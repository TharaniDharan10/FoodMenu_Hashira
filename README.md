# 🍽️ FoodMenu_Hashira - Indian Food Combo Generator

A Spring Boot backend application that intelligently generates daily food combos from Indian cuisine, featuring automatic meal planning with calorie optimization and uniqueness constraints.

## 🚀 Features

- **Daily Combo Generation**: Automatically generates 3 unique food combos per day
- **Calorie Optimization**: Each combo maintains 550-800 calories range
- **Uniqueness Guarantee**: No duplicate combos within a 3-day consecutive window
- **Indian Cuisine Focus**: Curated selection of popular Indian dishes
- **Weekly Planning**: Get combos for entire weeks at once
- **Smart Algorithm**: Balances popularity scores and nutritional requirements
- **RESTful APIs**: Clean and intuitive API endpoints
- **Cross-Origin Support**: Ready for frontend integration

## 🛠️ Tech Stack

- **Backend**: Spring Boot, Spring Data JPA
- **Database**: MySQL
- **Java Version**: 11+
- **Build Tool**: Maven

## 📊 Menu Statistics

- **Total Items**: 19 food items
- **Main Dishes**: 7 items (450-650 calories)
- **Side Dishes**: 6 items (100-350 calories)
- **Beverages**: 6 items (60-220 calories)
- **Taste Profiles**: Spicy, Savory, Sweet
- **Combos Per Day**: 3
- **Uniqueness Period**: 3 consecutive days

## 🍱 Sample Menu Items

### Main Dishes
- Paneer Butter Masala (450 cal, Spicy)
- Chicken Biryani (600 cal, Spicy)
- Vegetable Pulao (400 cal, Savory)
- Rajma Chawal (500 cal, Savory)
- Chole Bhature (650 cal, Spicy)
- Masala Dosa (480 cal, Savory)
- Grilled Sandwich (370 cal, Savory)

### Side Dishes
- Garlic Naan (200 cal, Savory)
- Mixed Veg Salad (150 cal, Sweet)
- French Fries (350 cal, Savory)
- Curd Rice (250 cal, Savory)
- Papad (100 cal, Savory)
- Paneer Tikka (300 cal, Spicy)

### Beverages
- Masala Chaas (100 cal, Spicy)
- Sweet Lassi (220 cal, Sweet)
- Lemon Soda (90 cal, Savory)
- Cold Coffee (180 cal, Sweet)
- Coconut Water (60 cal, Sweet)
- Iced Tea (120 cal, Sweet)

## 🔌 API Endpoints

### Base URL: `http://localhost:8080`

### Health & Information APIs

#### Health Check
```
GET /api/health
```
**Response**: Service status, version, and features information

#### Menu Statistics
```
GET /api/menu-stats
```
**Response**: Complete menu statistics and configuration details

### Combo Management APIs

#### Get Today's Combos
```
GET /api/combos/today
```
**Response**: 3 food combos for current date

#### Get Combos for Specific Date
```
GET /api/combos/date/{date}
```
**Parameters**: 
- `date`: Date in YYYY-MM-DD format (e.g., 2024-01-15)

**Example**: `GET /api/combos/date/2024-01-15`

#### Generate Combos for Date
```
POST /api/combos/generate/{date}
```
**Parameters**: 
- `date`: Date in YYYY-MM-DD format

**Description**: Forces generation of combos for the specified date

#### Get Weekly Combos
```
GET /api/combos/weekly/{startDate}
```
**Parameters**: 
- `startDate`: Start date in YYYY-MM-DD format

**Example**: `GET /api/combos/weekly/2024-01-15`
**Response**: 7 days of combos starting from the specified date

## 📋 API Response Format

### Combo Response Structure
```json
{
        "combo_id": 1,
        "main": "Paneer Butter Masala",
        "side": "Garlic Naan",
        "drink": "Iced Tea",
        "total_calories": 770,
        "popularity_score": 2.6,
        "reasoning": "Spicy profile fits Tuesday trends, popular choices (2.6), calorie target met (770 cal)"
    }
```

### Weekly Response Structure
```json
{
  "2025-07-28": [
    { "combo_id": 1, "main": "...", ... },
    { "combo_id": 2, "main": "...", ... },
    { "combo_id": 3, "main": "...", ... }
  ],
  "2025-07-29": [...],
  ...
}
```

## 🧮 Algorithm Details

### Combo Generation Logic

1. **Calorie Validation**: Ensures each combo falls within 550-800 calories
2. **Uniqueness Check**: Prevents duplicate combos within 3-day window
3. **Popularity Scoring**: Ranks combos based on individual item popularity
4. **Balanced Selection**: Chooses diverse combos avoiding item overlap when possible
5. **Taste Profile Analysis**: Determines dominant taste profile for reasoning

### Smart Features

- **Dynamic Generation**: Creates combos on-demand if not cached
- **Persistence**: Stores generated combos to avoid regeneration
- **Flexibility**: Allows manual regeneration via POST endpoints
- **Optimization**: Balances nutritional goals with taste preferences

## 🚀 Getting Started

### Prerequisites
- Java 11 or higher
- Maven 3.6+

### Installation & Setup

1. **Clone the repository**
```bash
git clone https://github.com/TharaniDharan10/FoodMenu_Hashira.git
cd FoodMenu_Hashira
```

2. **Build the project**
```bash
mvn clean install
```

3. **Run the application**
```bash
mvn spring-boot:run
```

4. **Access the application**
- Backend API: `http://localhost:8080`
- Health Check: `http://localhost:8080/api/health`

### Database Setup

Configure MySQL in `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/FoodMenu
spring.datasource.username=your_username
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
```

## 🔧 Configuration

### Application Properties
- **Port**: 8080 (default)
- **CORS**: Configured for `http://localhost:3000` (React frontend)
- **Combo Parameters**: 3 combos per day, 550-800 calorie range
- **Uniqueness Window**: 3 consecutive days

### Customization Options
- Modify calorie ranges in `ComboService.java`
- Add new food items via `DataLoader.java`
- Adjust combo count per day
- Configure different uniqueness periods

## 🧪 Testing the APIs

### Using cURL

```bash
# Get today's combos
curl http://localhost:8080/api/combos/today

# Get combos for specific date
curl http://localhost:8080/api/combos/date/2024-01-15

# Get weekly combos
curl http://localhost:8080/api/combos/weekly/2024-01-15

# Check health
curl http://localhost:8080/api/health

#Menu Stats
curl http://localhost:8080/api/menu-stats
```

### Using Postman
Import the endpoints and test with different date parameters to see the dynamic combo generation in action.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request


## 🙏 Acknowledgments

- Inspired by the need for automated meal planning
- Built with Spring Boot's powerful ecosystem
- Designed for Indian food enthusiasts

---

**Happy Eating! 🍽️**
