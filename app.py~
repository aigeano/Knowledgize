 # imports
from flask import Flask, render_template, request, redirect
import json, requests, sys
import summaly
import summarize
from nltk.corpus import wordnet as wn 

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def index():
    errors = ""
    if request.method == 'GET':
        return render_template("index.html",errors= errors)
    else :
        query = ""
        query = request.form['name']
        if query == "":
            return "No Query "
        url = "http://en.wikipedia.org/wiki/"+ query.lower()
        '''
        word = Word(query)
        word.synsets[:5]
        defi = word.definitions[0]()
        '''
        defi = ""
        summary = ""
        if defi :
            summary += defi

        text = summarize.summarize(url, query.lower())
        summary += text

        return redirect("tts-api.com/tts.mp3?q="+summary, code= 302 )





if __name__ == '__main__':
    app.debug = True
    app.run()
