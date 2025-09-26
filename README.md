# Real-Time Disease Tracking System

[![Live Demo](https://img.shields.io/badge/demo-offline-red.svg)](http://51.20.98.204)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://python.org)
[![Django](https://img.shields.io/badge/django-4.0+-green.svg)](https://djangoproject.com)

## 🎯 Overview

A comprehensive web-based platform that enables real-time disease outbreak tracking through user-generated data and interactive global mapping. Developed as part of Advanced Software Engineering coursework at University of Windsor.

**🚀 Problem Solved:** Traditional disease tracking systems rely on delayed government reports and lack real-time user input, creating gaps in early outbreak detection and localized health monitoring.

## ✨ Key Features

- **Real-time Disease Reporting**: Users can submit health symptoms and diagnoses with location data
- **Interactive Global Mapping**: Dynamic world map visualization with outbreak intensity indicators
- **Localized Insights**: OpenStreetMap integration for neighborhood-level disease tracking
- **Analytics Dashboard**: Comprehensive charts showing disease trends and patterns over time
- **User Authentication**: Secure registration and login system with role-based access
- **Mobile Responsive**: Bootstrap-powered responsive design for all devices
- **Real-time Notifications**: Location-based alerts for disease outbreaks in user areas
- **Data Privacy**: GDPR-compliant data handling with encryption and anonymization

## 🛠️ Technology Stack

**Backend:**
- Python 3.8+
- Django 4.0+ Framework
- Django REST Framework for APIs
- MySQL Database
- Docker containerization

**Frontend:**
- HTML5/CSS3
- JavaScript (ES6+)
- Bootstrap 5
- jQuery
- Interactive Mapping Libraries

**Infrastructure:**
- AWS EC2 cloud hosting
- Docker deployment
- MySQL database management

**Development Tools:**
- Git version control
- Manual testing procedures
- Iterative SDLC methodology

## 🏗️ System Architecture

The system follows a 3-tier architecture:
- **Presentation Layer**: Responsive web interface built with Django templates
- **Application Layer**: Django backend with REST APIs
- **Data Layer**: MySQL database with optimized schema design

## 📱 Screenshots

### Homepage with Global Disease Map
![Homepage showing interactive world map with disease outbreak data](screenshots/homepage.png)

### Disease Submission Interface
![User-friendly form for reporting symptoms and diagnoses](screenshots/disease-form.png)

### Analytics Dashboard
![Charts and visualizations showing disease trends over time](screenshots/analytics.png)

## 🚀 Quick Start

### Prerequisites
- Python 3.8 or higher
- MySQL 5.7 or higher
- Docker (optional, for containerized deployment)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/chowhanm25/real-time-disease-tracking.git
cd real-time-disease-tracking
```

2. **Set up virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure database**
```bash
# Update database settings in settings.py
python manage.py migrate
python manage.py createsuperuser
```

5. **Run development server**
```bash
python manage.py runserver
```

6. **Access the application**
Open `http://localhost:8000` in your browser

### Docker Deployment

```bash
# Build and run with Docker Compose
docker-compose up --build
```

## 📖 Usage

### For General Users
1. **Register/Login**: Create an account or sign in to existing account
2. **View Global Map**: Explore disease outbreaks worldwide on the interactive map
3. **Submit Reports**: Report symptoms and diagnoses using the submission form
4. **Get Notifications**: Receive alerts about disease outbreaks in your area
5. **Analyze Trends**: Use the analytics dashboard to understand disease patterns

### For Healthcare Authorities
- Access aggregated data for public health decision-making
- Monitor regional outbreak patterns
- Export anonymized data for research purposes

### For Researchers
- Access historical and real-time disease data
- Analyze outbreak patterns for academic research
- Develop AI/ML models for disease prediction

## 🧪 Testing

The project uses manual testing procedures covering:
- **End-to-End Testing**: User registration, login, and disease reporting workflows
- **Integration Testing**: Frontend-backend API integration
- **Performance Testing**: System behavior under high traffic conditions
- **Usability Testing**: Interface accessibility and user experience validation

To run tests:
```bash
python manage.py test
```

## 📊 Project Metrics

- **Development Timeline**: 10 weeks (January - March 2025)
- **Team Size**: 4 developers (SPLASH Group 1)
- **System Uptime**: 99.9% target availability
- **Response Time**: Sub-second map updates
- **Data Security**: End-to-end encryption implementation

## 🔐 Security Features

- **Data Encryption**: End-to-end encryption for all sensitive health data
- **User Authentication**: Secure login with role-based access control
- **Privacy Compliance**: GDPR-compliant data handling and anonymization
- **Input Validation**: Comprehensive data validation to prevent false reporting
- **Rate Limiting**: Protection against spam and abuse

## 🌟 Future Enhancements

### Immediate Roadmap (Next 3 months)
- **AI Integration**: Machine learning for outbreak prediction
- **Mobile App**: React Native companion application
- **Advanced Analytics**: Predictive modeling and trend forecasting
- **API Gateway**: Public API for researchers and third parties

### Long-term Vision (6-12 months)
- **Blockchain Integration**: Immutable health data records
- **IoT Device Support**: Wearable health monitor integration
- **Multi-language Support**: Internationalization for global deployment
- **3D Visualization**: Advanced mapping with AR/VR integration

## 👥 Team & Contributions

**SPLASH Group 1 - University of Windsor**
- **Ahmet Furkan Eren**: Backend Development & API Implementation
- **Muhammad Nauman Shafique**: Frontend Development & UI Design
- **Soban Abid**: Database Management & Architecture
- **Munna Chowhan**: Quality Assurance & Project Coordination

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

For support, email the development team or create an issue in this repository.

## 🙏 Acknowledgments

- University of Windsor School of Computer Science
- COMP8117 Advanced Software Engineering Course
- World Health Organization for disease data standards
- Centers for Disease Control and Prevention for research insights

---

**⭐ Star this repository if you find it helpful!**

## 📈 Project Impact

This system addresses critical gaps in global health monitoring by:
- Enabling early disease outbreak detection through user-generated data
- Providing localized health risk information to communities
- Supporting public health authorities with real-time data aggregation
- Facilitating academic research through anonymized health datasets
- Improving public health response times during emergencies

**Built with ❤️ by SPLASH Group 1**