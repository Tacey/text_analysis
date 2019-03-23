# text_analysis

0. Project description

The purpose of this project is to provide a report on the textual analysis of the files in the provided set, with analysis techniques such as  parts-of-speech, type/token ratios and n-grams.

1. Introduction of 3 texts

Our second text is a historical novel by Thomas Hardy called The Trumpet-Major. This novel was published in 1880 and set during the Napoleonic era centered around European war in a time of war and uncertainty. From our groups first glance at the text, the novel was heavily filled with dialogue and vocabulary that would be rarely found in modern day.

Our third and last provided text is a document titled XAR. It contains three main sections and the text of this corpus tends to be grouped by an underlying theme of computer science topics. These topics are academically or educationally inclined with technical jargon.

2. Preprocessing

Our group tackled preprocessing in segments beginning with the simplest document that we were given. On first examination, we decided that our second text, trumpets would be the best place to start. Looking through the text, we concluded that taking out copyright information, prefaces, footnotes and chapter headings would be the first course of action. Since a lot of this was in large sections and could be manually removed, it served to be simple and straightforward. We parsed through our resulting text and began seeing some interesting words to note. The author often used ‘-’ and ‘--’ to separate words or portions of a word and thus, if we simply replaced all non alphanumeric characters with a new line, it would separate words that were intended to be whole. Conversely, if we merely removed all hyphens there were cases where the authors chose to use the double hyphens between two words and thus concatenate when unnecessary. (Script 3 in Appendix)

With the above script, we managed to remove hyphens and apostrophes while replacing double hyphens and all other non alphanumeric with a space. We made sure to leave full stops, exclamation marks and question marks to denote the end of a sentence as we needed this for future data collection.

As for our next text, our group tackled ‘nonfiction.txt’. A large portion of the preprocessing required stood in the form of removing references, figures, and a repeated NULL within the text. Upon further inspection, we found that the NULL were placed where the original text would have images or figures. For the references, since they were placed in large contiguous sections, it proved to be simple to manually remove. Additionally, for the references to figures, we left the word ‘Figures’ in the text while taking note to account for their irregular structure (ie Figure 2.13) when we collected data for sentence length.

Our third and last provided text proved to be the hardest to process. XAR was filled with many references, code, and large collections of numbers. This proved to be very difficult to manage because there wasn’t a general rule that could deal with each situation properly. We tackled this by initially removing the repetitive header at the beginning of the first section of text followed by large sections of references and table of contents. For URLs in the text, we replaced all the instances of them with a generic string ‘SomeWebSite’ to preserve the mention of a website while removing clutter and generalizing them as one.

Using Script 4, we were able to identify any URL that starts with ‘www’, ‘https’ or ‘http’ using a regular expression. After dealing with the URLs, the next logical step was to clean up meaningless special characters. Since XAR was filled with mathematical formulas, equations and snippets of code, merely replacing non alphabetical characters with spaces would result in collections of standalone words or characters. For example, if we remove non alphabetical characters in “x^2 + y^2 = r^2”, the corresponding result would be “x 2 y 2 r 2”. This would undermine the accuracy of our later data collection(i.e. Word count, sentence length, type/token ratio, etc). One solution was to eliminate any word with length less than a certain threshold.

With another script, Script 5,  any word with length less than 1 was removed and a new list of words was achieved in the form of lines. This also solved the problem where extra spaces found in between letters(i.e. “C o m m u n i c a t e”). Note that the drawback of this method was any actual word with length 1 was also removed, for example, the article ‘a’.


3. Similarities Between Texts

Our analysis found some shared properties in terms of tokens. Trumpet and XAR shared a type/token ratio at around 0.08, while nonfiction had a type token ratio 0.2. Our group believes this is due to the length of the document where XAR and trumpet are substantially longer than the nonfiction text. When is comes to unique tokens, the three files where consist in their average unique token length being 12.5 characters and this trend held even for tokens used 3 or less times.

The three texts seemed to be consistent in their average word length. Looking at the total number of characters divided by total number of words XAR gave an average 5.93 characters, Nonfiction had an average of  6.46 characters, and Trumpet had an average 5.37.  Average sentences showed a shared trend as well  with XAR averaging 18.89 words per sentence, Nonfiction averaging 15.86 words per sentence, and Trumpet averaging 16.6 words. The minor deviation of XAR could be attributed to our counting method, where files were put into lines based on periods, exclamation marks, and questions marks. Quotes in trumpets would have skewed results and nonfiction has some potential biases.

We found similar results between shorter texts and longer ones in another, related analysis; the ratio of unique n-grams to total n-grams in the files. These results fell mostly in line with type/token ratio results; by and large, there was a larger percentage of unique n-grams in the shorter files than the longer ones. Roughly 70% of nonfiction 2-grams were unique,  verses about 50% unique in the case of trumpet and XAR, and nonfiction contained about 95% unique 3-grams whereas trumpet and XAR ranged from 85 to 90%. This second degree of correlation affirms the suggestion that the length of the files played a large role in the ratio of unique types or n-grams compared to their totals.
