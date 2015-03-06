# ship-computer
Ship Computer scripts for Voice Attack -> Q&amp;A -> Text-To-Speech system.

Preliminary design phase (Alpha)

Objectives:

- Speak a "command" (query) preceded by the word "Computer"
- Have Voice Attack listen for the keyword "Computer" in speech recognition, passing "command" to an additional script
- Script converts the "command" for a search engine, executes search
- Search results are stripped to text only, and passed to Text-To-Speech program.

It's suggested to utilize a macro system to assist with the running of the TTS, if necessary.

Script notes:

So far curl and powershell do quite enough for us with this one-liner:

C:\> curl --silent -kX GET http://www.answers.com/Q/What_is_a_binary_star|FINDSTR "og:description" 2>nul|POWERSHELL -command "echo $input | %{$_ -repl
ace '<.*?Answer'}|%{$_ -replace '>$'}"

 a stellar system consisting of two stars that are held together by their mutual gravitational attraction and revolve around a common point, called the center
of mass following kepler's laws."

Update 3/6/2015:  

- Will need to account for query response for og.description: "Answers - The Most Trusted Place for Answering Life's Questions" - as this is essentially the site saying it couldn't find your question, this should copy something to the effect of "Unable to identify your query, commander"

- Will require Zabaware's TTS program to be open, in order to perform this.

- Can probably just make use CLIP.EXE to put response text into the clipboard, the TTS reads back instantly: C:\> echo "TEST" | CLIP
