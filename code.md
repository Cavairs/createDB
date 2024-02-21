```sql
-- Создание таблицы "Жанры"
CREATE TABLE IF NOT EXISTS genre (
  genreID INT PRIMARY KEY,
  name_genre VARCHAR(255)
);

-- Создание таблицы "Исполнители"
CREATE TABLE IF NOT EXISTS artist (
  artistID INT PRIMARY KEY,
  nameArtist VARCHAR(255)
);

-- Создание таблицы "Исполнитель_Жанр" для связи исполнителей и жанров
CREATE TABLE IF NOT EXISTS artist_genre (
  artistID INT,
  genreID INT,
  FOREIGN KEY (artistID) REFERENCES artist (artistID),
  FOREIGN KEY (genreID) REFERENCES genre (genreID)
);

-- Создание таблицы "Альбомы"
CREATE TABLE IF NOT EXISTS albums (
  albumID INT PRIMARY KEY,
  name_album VARCHAR(255),
  year_release INT
);

-- Создание таблицы "Исполнитель_Альбом" для связи исполнителей и альбомов
CREATE TABLE IF NOT EXISTS artist_album (
  artistID INT,
  albumID INT,
  FOREIGN KEY (artistID) REFERENCES artist (artistID),
  FOREIGN KEY (albumID) REFERENCES albums (albumID)
);

-- Создание таблицы "Треки"
CREATE TABLE IF NOT EXISTS tracks (
  trackID INT PRIMARY KEY,
  name_track VARCHAR(255),
  time_lap TIME,
  albumID INT,
  FOREIGN KEY (albumID) REFERENCES albums (albumID)
);

-- Создание таблицы "Сборники"
CREATE TABLE IF NOT EXISTS collections (
  collectionID INT PRIMARY KEY,
  name_colections VARCHAR(255),
  year_release INT
);

-- Создание таблицы "Трек_Сборник" для связи треков и сборников
CREATE TABLE IF NOT EXISTS track_collection (
  trackID INT,
  collectionID INT,
  FOREIGN KEY (trackID) REFERENCES tracks (trackID),
  FOREIGN KEY (collectionID) REFERENCES collections (collectionID)
);
