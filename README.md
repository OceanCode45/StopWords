# StopWords for the bot
Stop Words for the Top Phrases bot

About the bot: 
The bot is a Python script that analyzes the top comments from a specified number of hot posts in a given subreddit and identifies the most common word pairs (phrases) used in those comments. It then generates a bar chart displaying the top phrases and their frequencies, and posts the chart as an image to another specified subreddit.

The script uses the PRAW (Python Reddit API Wrapper) library to interact with the Reddit API, as well as other libraries like Pandas, Seaborn, and Matplotlib for data manipulation and visualization.


In this bot, ignored words are called "Stop Words." These are common words that are often considered uninformative or irrelevant for text analysis because they don't carry much meaning by themselves. Examples of such words include "the," "and," and "i." The purpose of excluding these words is to focus on more meaningful word pairs (phrases) in the comments.

The script defines a set called IGNORED_WORDS that contains these stop words. When processing the comments and extracting word pairs, the script checks each word in the pair against the IGNORED_WORDS set. If either word is found in the set, the word pair is not included in the phrase count.

By ignoring these common stop words, the script can produce a more meaningful analysis of the top phrases used in the comments, concentrating on word pairs that provide more insight into the content and trends within the discussion.


The complete list of stop words:

IGNORED_WORDS = {
"the", "and", "a", "an", "of", "to", "in", "is", "that", "it", "with", "for", "on", "at", "by", "this",
"from", "not", "be", "are", "you", "or", "was", "but", "if", "they", "have", "had", "has", "will", "can",
"am", "who", "what", "when", "where", "why", "how", "which", "there", "their", "we", "our", "us",
"I", "me", "myself", "we", "our", "ours", "ourselves", "you", "your", "yours", "yourself", "yourselves",
"he", "him", "his", "himself", "she", "her", "hers", "herself", "it", "its", "itself", "they", "them",
"their", "theirs", "themselves", "what", "which", "who", "whom", "this", "that", "these", "those", "am",
"is", "are", "was", "were", "be", "been", "being", "have", "has", "had", "having", "do", "does", "did",
"doing", "but", "if", "or", "because", "as", "until", "while", "about", "against", "between", "into",
"through", "during", "before", "after", "above", "below", "up", "down", "out", "off", "over", "under",
"again", "further", "then", "once", "here", "there", "when", "where", "why", "how", "all", "any", "both",
"each", "few", "more", "most", "other", "some", "such", "no", "nor", "only", "own", "same", "so", "than",
"too", "very", "just", "don", "should", "now", "a", "able", "about", "above", "abst", "accordance", "according", "accordingly", "across", "act", "actually",
"added", "adj", "affected", "affecting", "affects", "after", "afterwards", "again", "against", "ah", "all",
"almost", "alone", "along", "already", "also", "although", "always", "am", "among", "amongst", "an", "and",
"announce", "another", "any", "anybody", "anyhow", "anymore", "anyone", "anything", "anyway", "anyways",
"anywhere", "apparently", "approximately", "are", "aren", "arent", "arise", "around", "as", "aside", "ask",
"asking", "at", "auth", "available", "away", "awfully", "b", "back", "be", "became", "because", "become",
"becomes", "becoming", "been", "before", "beforehand", "begin", "beginning", "beginnings", "begins", "behind",
"being", "believe", "below", "beside", "besides", "between", "beyond", "biol", "both", "brief", "briefly",
"but", "by", "c", "ca", "came", "can", "cannot", "can't", "cause", "causes", "certain", "certainly", "co",
"com", "come", "comes", "contain", "containing", "contains", "could", "couldnt", "d", "date", "did", "didn't",
"different", "do", "does", "doesn't", "doing", "done", "don't", "down", "downwards", "due", "during", "e",
"each", "ed", "edu", "effect", "eg", "eight", "eighty", "either", "else", "elsewhere", "end", "ending",
"enough", "especially", "et", "et-al", "etc", "even", "ever", "every", "everybody", "everyone", "everything",
"everywhere", "ex", "except", "f", "far", "few", "ff", "fifth", "first", "five", "fix", "followed",
"following", "follows", "for", "former", "formerly", "forth", "found", "four", "from", "further",
"furthermore", "g", "gave", "get", "gets", "getting", "give", "given", "gives", "giving", "go", "goes",
"gone", "got", "gotten", "h", "had", "happens", "hardly", "has", "hasn't", "have", "haven't", "having",
"he", "hed", "hence", "her", "here", "hereafter", "hereby", "herein", "heres", "hereupon", "hers", "herself",
"hes", "hi", "hid", "him", "himself", "his", "hither", "home", "how", "hundred", "i", "id", "ie", "if", "i'll", "im", "immediate", "immediately", "importance", "important",
"in", "inc", "indeed", "index", "information", "instead", "into", "invention", "inward", "is", "isn't", "it",
"itd", "it'll", "its", "itself", "i've", "j", "just", "k", "keep", "keeps", "kept", "kg", "km", "know",
"known", "knows", "l", "largely", "last", "lately", "later", "latter", "latterly", "least", "less", "lest",
"let", "lets", "like", "liked", "likely", "line", "little", "ll", "look", "looking", "looks", "ltd", "m",
"made", "mainly", "make", "makes", "many", "may", "maybe", "me", "mean", "means", "meantime", "meanwhile",
"merely", "mg", "might", "million", "miss", "ml", "more", "moreover", "most", "mostly", "mr", "mrs", "much",
"mug", "must", "my", "myself", "n", "na", "name", "namely", "nay", "nd", "near", "nearly", "necessarily",
"necessary", "need", "needs", "neither", "never", "nevertheless", "new", "next", "nine", "ninety", "no",
"nobody", "non", "none", "nonetheless", "noone", "nor", "normally", "nos", "not", "noted", "nothing", "now",
"nowhere", "o", "obtain", "obtained", "obviously", "of", "off", "often", "oh", "ok", "okay", "old", "omitted",
"on", "once", "one", "ones", "only", "onto", "or", "ord", "other", "others", "otherwise", "ought", "our",
"ours", "ourselves", "out", "outside", "over", "overall", "owing", "own", "p", "page", "pages", "part",
"particular", "particularly", "past", "per", "perhaps", "placed", "please", "plus", "poorly", "possible",
"possibly", "potentially", "pp", "predominantly", "present", "previously", "primarily", "probably", "promptly",
"proud", "provides", "put", "q", "que", "quickly", "quite", "qv", "r", "ran", "rather", "rd", "re", "readily",
"really", "recent", "recently", "ref", "refs", "regarding", "regardless", "regards", "related", "relatively",
"research", "respectively", "resulted", "resulting", "results", "right", "run", "s", "said", "same", "saw",
"say", "saying", "says", "sec", "section", "see", "seeing", "seem", "seemed", "seems", "seen", "self", "selves", "sent", "seven", "several", "shall", "she", "shed", "she'll",
"shes", "should", "shouldn't", "show", "showed", "shown", "showns", "shows", "significant", "significantly",
"similar", "similarly", "since", "six", "slightly", "so", "some", "somebody", "somehow", "someone", "somethan",
"something", "sometime", "sometimes", "somewhat", "somewhere", "soon", "sorry", "specifically", "specified",
"specify", "specifying", "still", "stop", "strongly", "sub", "substantially", "successfully", "such",
"sufficiently", "suggest", "sup", "sure", "t", "take", "taken", "taking", "tell", "tends", "th", "than",
"thank", "thanks", "thanx", "that", "that'll", "thats", "that've", "the", "their", "theirs", "them",
"themselves", "then", "thence", "there", "thereafter", "thereby", "thered", "therefore", "therein", "there'll",
"thereof", "therere", "theres", "thereto", "thereupon", "there've", "these", "they", "theyd", "they'll",
"theyre", "they've", "think", "this", "those", "thou", "though", "thoughh", "thousand", "throug", "through",
"throughout", "thru", "thus", "til", "tip", "to", "together", "too", "took", "toward", "towards", "tried",
"tries", "truly", "try", "trying", "ts", "twice", "two", "u", "un", "under", "unfortunately", "unless",
"unlike", "unlikely", "until", "unto", "up", "upon", "ups", "us", "use", "used", "useful", "usefully",
"usefulness", "uses", "using", "usually", "v", "value", "various", "ve", "very", "via", "viz", "vol", "vols",
"vs", "w", "want", "wants", "was", "wasnt", "way", "we", "wed", "welcome", "we'll", "went", "were", "werent",
"we've", "what", "whatever", "what'll", "whats", "when", "whence", "whenever", "where", "whereafter",
"whereas", "whereby", "wherein", "wheres", "whereupon", "wherever", "whether", "which", "while", "whim",
"whither", "who", "whod", "whoever", "whole", "who'll", "whom", "whomever", "whos", "whose", "why", "widely",
"willing", "wish", "with", "within", "without", "wont", "words", "world", "would", "wouldnt", "www", "x", "y",
"yes", "yet", "you'd", "you'll", "you're", "you've", "your", "yours", "yourself", "yourselves", "z", "zero", "a", "able",
"about", "above", "abst", "accordance", "according", "accordingly", "across", "act", "actually", "added",
"adj", "affected", "affecting", "affects", "afterwards", "ah", "almost", "alone", "along", "already", "also",
"although", "always", "among", "amongst", "an", "announce", "another", "any", "anybody", "anyhow", "anymore",
"anyone", "anything", "anyway", "anyways", "anywhere", "apparently", "approximately", "aren", "arent", "arise",
"aside", "ask", "asking", "auth", "away", "awfully", "back", "became", "because", "become", "becomes",
"becoming", "beforehand", "begin", "beginning", "beginnings", "behind", "believe", "below", "beside",
"besides", "between", "beyond", "biol", "brief", "briefly", "ca", "came", "cannot", "can't", "cause",
"causes", "certain", "certainly", "co", "com", "come", "contain", "containing", "contains", "couldnt",
"date", "different", "done", "down", "downwards", "due", "e", "each", "ed", "edu", "effect", "eg", "eight",
"eighty", "either", "else", "elsewhere", "end", "ending", "enough", "especially", "et", "et-al", "etc",
"even", "ever", "every", "everybody", "everyone", "everything", "everywhere", "except", "far", "few",
"ff", "fifth", "first", "five", "fix", "followed", "following", "follows", "former", "formerly", "forth",
"found", "four", "from", "further", "furthermore", "gave", "get", "gets", "getting", "give", "given",
"gives", "giving", "go", "gone", "got", "gotten", "happens", "hardly", "hed", "hence", "hereafter",
"hereby", "herein", "heres", "hereupon", "hes", "hi", "hid", "himself", "his", "hither", "hopefully",
"howbeit", "however", "hundred", "id", "ie", "im", "immediate", "immediately", "importance", "important",
"inc", "indeed", "index", "information", "instead", "invention", "inward", "itd", "it'll", "j", "k", "keep",
"keeps", "kept", "kg", "km", "known", "l", "largely", "last", "lately", "later", "latter", "latterly",
"least", "less", "lest", "lets", "like", "liked", "likely", "line", "little", "look", "looking", "people", "https", "http", "www"
}
