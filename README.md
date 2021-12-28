# Docker - PostgreSQL - PgAdmin
version: '3'

services:
  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: "Postgres2019!"
    ports:
      - "15432:5432"
    volumes:
      - /PostgreSQL:/var/lib/postgresql/data 
    networks:
      - postgres-network
      
  web:
    image: dpage/pgadmin4
    environment:
      PGADMIN_DEFAULT_EMAIL: "seu-email-aqui"
      PGADMIN_DEFAULT_PASSWORD: "PgAdmin2019!"
    ports:
      - "16543:80"
    depends_on:
      - db
    networks:
      - postgres-network

networks: 
  postgres-network:
    driver: bridge

### Execução
- docker-compose up -d