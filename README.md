# mahout-tutorial
Screen recording can be found in following link

https://drive.google.com/file/d/1c9x-YijQEHc0AZvI3Ac-JmSKCajyJ4vN/view?usp=sharing

# Steps

wget http://files.grouplens.org/datasets/movielens/ml-1m.zip

unzip ml-1m.zip

cat ml-1m/ratings.dat | sed 's/::/,/g' | cut -f1-3 -d, > ratings.csv

hadoop fs -put ratings.csv /ratings.csv

mahout recommenditembased --input /ratings.csv --output recommendations --numRecommendations 10 --outputPathForSimilarityMatrix similarity-matrix --similarityClassname SIMILARITY_COSINE

hadoop fs -ls recommendations

hadoop fs -cat recommendations/part-r-00000 | head

wget http://download.redis.io/releases/redis-2.8.7.tar.gz

tar xzf redis-2.8.7.tar.gz

cd redis-2.8.7

make

./src/redis-server &

twistd -noy hello.py &

curl localhost:8087/37

