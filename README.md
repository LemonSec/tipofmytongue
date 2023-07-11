# tipofmytongue
Grepable export of all sub-titles files from infocon.org. Allowing you to search for keywords from presentations.

This repo exists because I could never remember what presentation I watched that had the thing I was looking for. Have you ever wished you could quickly find all the presentations on PLCs? Or maybe you're interested in learning about threat actors who use rclone?  Thanks to the enormous repository of conference presentations available on infocon.org, we've been able to implement a convenient solution using grep to search for keywords contained within subtitle files. Infocon.org deserves all the credit not only for housing such a wealth of information but also for including subtitles for each presentation.

How It Works

We scraped subtitle files from infocon.org and arranged them in corresponding folders. These subtitle files contain all the textual information that is spoken in the presentations, making them the perfect candidate for searching specific topics or keywords.

Searching for a Keyword

The real magic happens when we bring grep into the equation. Grep is a powerful command-line utility that allows you to search for specific patterns within files. In our case, we use it to search the subtitle files for our keyword or phrase. Here are some common grep one-liners that you can use to find your desired content.

   If you're searching for a simple keyword, say "mega", and we also want the line that tells us the exact time the keyword is mentioned the command would be:


grep -r -B 1 "mega" .

The -r option tells grep to search recursively in all files and directories under the current directory. The "." denotes the current directory.

![grep b1](https://github.com/LemonSec/tipofmytongue/assets/33465511/747cac39-228b-4f61-a799-3f20f3c8b9b4)

Search for files that contain multiple keywords together and then highlight the file name.

replace the words rclone and mega with your keywords. This will search for all instances of the keywords together and then highlight the filename of the presentation in blue.

grep -lir 'rclone' . | while IFS= read -r file; do grep -iq 'plc' "$file" && grep --color=always -i 'rclone\|megasync' "$file" | sed 's/<[^>]*>//g' && echo -e "\e[96m$file\e[0m"; done


![ransom](https://github.com/LemonSec/tipofmytongue/assets/33465511/364da3f4-be5c-4edc-9e7b-404fa374af99)

Once you find the corresponding talk you're looking for. Search for it on YouTube or
Navigate to https://infocon.org/cons/
Select the conference and follow the directories down until you find the mp4. for the presentation you are interested in watching and download the file
![infocon](https://github.com/LemonSec/tipofmytongue/assets/33465511/2a3a6fe9-152f-4c9b-b7f4-6a0f8742d913)
