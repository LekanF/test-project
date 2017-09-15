download:
	mkdir -p data
	 cd ./data
	 wget www.derekruths.com/static/reading_tweets/books_tweets100000.txt.gz   #-O data/books_tweets100000.txt.gz
	 gunzip books_tweets100000.txt.gz 
#prep:
	cat books_tweets100000.txt | jq -r '" \(.user.id)\t\(.user.created_at) \t\(.user.lang) \t\(.text)"' >> book_tweets.tsv
	cut  -f 2 book_tweets.tsv | cut -d ' ' -f 2,6  | grep -c "Oct 2012" >> tweetsOct2012.tsv
	#grep -i "Oct 23" book_tweets.tsv >> tweetsOct2012.tsv
	grep -i "#gameofthrones" book_tweets.tsv >> tweets_got.tsv
#analyze:
	echo "Tweets with Russian Language: " >> results.txt
	cut  -f 3 book_tweets.tsv | grep -c "ru" >> results.txt
	#echo "\n" >> results.txt
	echo "How many tweets from Aug 2016: " >> results.txt
	cut  -f 2 book_tweets.tsv  >> time.txt 
	cut -d ' ' -f 2,6 time.txt | grep -c "Aug 2016" >> results.txt
#	echo "\n" >> results.txt
	echo "How many tweets contain a retweet: " >> results.txt
	cut  -f 4 book_tweets.tsv | grep -c "RT" >> results.txt # -d \$'\t' tab delimiter
	#echo "\n" >> results.txt
	echo "How many tweets mention #gameofthrones" >> results.txt
	cut  -f 4 book_tweets.tsv | grep -ic "gameofthrones" >> results.txt
	#echo "\n" >> results.txt
	
#remove:
	rm books_tweets100000.txt
