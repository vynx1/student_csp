---
layout: blogs
title: Data Structures Project
description: A Notebook reviewing Data Structures. 
type: tangibles
courses: {'csse': {'week': 1}, 'csp': {'week': 4}, 'csa': {'week': 0}}
categories: ['C4.1']
---
<html lang="en" style="padding-right: 300px">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Data Structure Blog</title>
    <link rel="stylesheet"
        href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/10.0.3/styles/default.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/10.0.3/highlight.min.js"></script>
    <script>hljs.initHighlightingOnLoad();</script>
</head>
<body style="width: 550px">
    <!-- Intro Section -->
    <section>
        <h1>Welcome to My Data Structure Blog!</h1>
        <p>In this blog, I'll be sharing my experiences and insights from working on two exciting projects: creating a Spotify clone and developing an image classification machine learning model with PyTorch.</p>
        <p>During the course of the TRimester I developed a Machine Learning Classfication Model, and was given the oppurtunity to combine my code with my classmates and integrate it into one project. </p>
        <!-- <img style="width: 20px, height: 20px," src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/2048px-Spotify_logo_without_text.svg.png" alt="Spotify Logo">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/PyTorch_logo_icon.svg/1200px-PyTorch_logo_icon.svg.png" alt="PyTorch Logo"> -->
    </section>
    <!-- Collections Section -->
    <section >
        <h2>Collections</h2>
        <p>For the Spotify clone project, I developed a SQLite database to manage all of my songs data. Below is the code snippet for initializing the database. By creating a SQLITE Table from scratch It made implementing the table signifcantly easier. </p>
        <p>Here's a visualization of my SQLite database:</p>
        <iframe src="https://drive.google.com/file/d/1rED-1nOZ3sVz6j1ZOa6A3Qg4st1iQO4e/preview" width="640" height="480" allow="autoplay"></iframe>
        <h3>Here's how I made the table</h3>
        <pre>
        <code class="python" >
    class Song(db.Model):  
    
    __tablename__ = 'songs'  

    id = db.Column(db.Integer, primary_key=True)
    _name = db.Column(db.String(255), unique=False, nullable=False)
    _url = db.Column(db.String(255), unique = False, nullable=False)
    _description = db.Column(db.String(255), unique=True, nullable=False)
    _uri = db.Column(db.String(255), unique=False, nullable=False)
    _tokens = db.Column(db.Integer)
    
    def __init__(self, name, url, description, uri, tokens):
        self._name = name
        self._description = description
        self._url = url  # Corrected assignment to _url
        self._uri = uri
        self._tokens = tokens

    def to_dict(self):
        return {"id": self.id, "_name": self._name, "url": self._url, "_description": self._description, "_uri": self._uri, "_tokens": self._tokens}
    
    def update(self, name="", url="", uri=""):
        """only updates values with length"""
        if len(name) > 0:
            self.name = name
        if len(url) > 0:
            self.url = uri
        if len(uri) > 0:
            self.uri = uri
        db.session.commit()
        return self

# Function to create songs, store them in JSON format, and return the created songs
def initSongs():
    with app.app_context():

        db.create_all()

        

        songs_data = [
    {'name': 'FEIN', 'url': '/audios/FEIN.mp3', 'description': 'Travis Scott_', 'uri': 'data:image/jpeg;base64,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', 'tokens':'1'},
    {'name':'Creepin', 'url':'/audios/CREEP.mp3', 'description':'The Weeknd', 'uri':'https://i1.sndcdn.com/artworks-sWl8wb2Zk1xthx3m-39RYRQ-t500x500.jpg', 'tokens':'2'},
    {'name':'Role Model', 'url':'', 'description':' Brent Fiaiyaz', 'uri':'https://i1.sndcdn.com/artworks-O2SRR9SCgyRq4u4v-eAojjA-t500x500.jpg', 'tokens':'4'},
    {'name':'Right my Wrongs', 'url':'', 'description':' Bryson Tiller', 'uri':'https://i.scdn.co/image/ab67616d0000b273d5f3cea8affdca01a0dc754f', 'tokens':'5'},
    {'name':'Roar', 'url':'', 'description':' Katy Perry', 'uri':'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT_Y92S1N976xSO57PbyPinyoJ8IVnqGPFhLQ&usqp=CAU', 'tokens':'6'},
    {'name':'Shake it Off', 'url':'/audios/SHAKE.mp3', 'description':' Taylor Swift', 'uri':'https://pyxis.nymag.com/v1/imgs/2d9/6f5/3f8dbd63613637b7843e4653ff548503b9-tay--.w710.jpg', 'tokens':'9'},
    {'name':'Often', 'url':'/audios/OFTEN.mp3', 'description':' The Weeknd_', 'uri':'https://cdns-images.dzcdn.net/images/cover/eea9f7fc913300e40307a0ff70dc73cf/350x350.jpg', 'tokens':'8'},
    {'name':'Thank God', 'url':'', 'description':' Travis Scott', 'uri':'data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBw0NDQ0NDg0NDQ0NDQ4NDQ0ODQ8ODQ0OFhEWFhURFRUYHSghGBomGxUVITEhJSkrLi4uFx8zODMwNygtLysBCgoKDg0OFxAQFy0eHR0rKy0rKy0tLS0rKy0rLS0rLS0tLSstLS0tLS0tLS0tLSstLS0rLTctLSstLS0tLSs3K//AABEIAOEA4QMBIgACEQEDEQH/xAAbAAEBAAIDAQAAAAAAAAAAAAAAAQMFAgQGB//EAD0QAAICAQMCBAMEBggHAAAAAAABAgMRBBIhBTETQVFhBiJxMkJSgRQjkbHR8AczYnKCk6HBFRZDVKKy0v/EABcBAQEBAQAAAAAAAAAAAAAAAAABAgP/xAAcEQEBAQACAwEAAAAAAAAAAAAAARESQQIhMVH/2gAMAwEAAhEDEQA/APigAKoAQCgAAAAAAAAACFIUAAQCgEAFAAAAAAAAAAAAAQAAUAAAAAAAAAAAAAAAAhQABAKAQCgAAQoAAAAAAAAAEKQCghQAAAAACFAAAAAAAAIUAAAABAKQoAAEAoIUAAAAAAEKQAUAAAAAAAAAACACghQAIUCFIUAAQCgAAAAAAAAAAAAICkAoAAAgAoAAJZaXm+Ec3Da2pd8eXPOOEcDJuykscrP5r0A4CSDXp+wSA4gAAUhQAAAAEAoAAAEAoAAAAAAABAAKAABCgAAAATBAOQkRdigcQAAKAAIUACFIBQQoAhQAAAAAAAAAAAAAAACAUAAAAARUQBFnHDwcTsWRzFPzRgCoAUCFAAAAACHOFUpdl+5AcQZJaexc7JY9Uty/0MbWAAAAAAAAAABAKAAABAKAAAAAAADs6dpvDLrdK4Ymvsvh+zMUF2PS6fTxvp2v7yaXruRFjyhTnfU65yhLvF4+vuYyooIAKAEAM9M8Psn+RhwZo7oxjJSall9uGkQj6N0XSdKt6LrNRdF06rT027WntjbY44rg49nmTivXk8r1zoNldNN+PmdUd8cNNwUFtl9cLt7GTS9QsuVGjlKM61bC2U+U7IxhKXhyS+1z5900d7qnUvFeyUVFxs3YTeGvtNfXCKWdvFAs0k2o/Zy1H1xnggAAAAAAIABQAAAIBQAAAAAAAc65eXuen6TYo1yk5NJdmucNNM8obPTa3FFkH5uP5Eqyu58U0xbr1EEvmW2zHZPun9HzyaE3fTeobJx3rdDGHF9mv4DrfS4LN+mj+q5c6087P7S/s+3kSVbO2kBAaZUAIAd6DnOEFKUJ7X8sV/WY/B6+/wDLOmln+Jm0stsoyTeV/LIRuug9Unp7swjDMk4fMlJL0f8APuY+oayE77bPklGW5ONblDw+eZ9vxqOO+cGqjZLL29329snO3XWeF+jqX6vc5NJLmWOefJcdg1rpIoBWQG56X8La/V1u2ijdDOE5SUN3GeM9zrdS6FrdJj9I01tSaypOO6GP70comxcrXgAqICkAoIUAAAIUAAAAAAADIAHOFmOPI7vT+pSqeH80fL2NeQmGtp1PRV7FqKJRdcnida+1VL+H7jWxhKWcRlLHfEW8fsOdWolGMo8NTWGn+89b8FdXjiWlsaUZ8QWIpZxwucD41JLXjSnoviHpihfunDw1N+qSk/qY6+kUyinmSbJpwrRJnJT+h6Xqnwo6KYWuUk5pOCltxNN+WHkwaX4VunjduWe2I5LsONaOFmOfPnBl6d06/VWKumuU5N4bS+WPu2e20H9H+F42onJVRTk/lxlL3Z6HSavQ6SpR08q8ecm488epLVnj+tBo/g7Q1vZqVqbZRS8SdcsVwb9ks447njuvUaerVWQ0zlKiMltcpbn784PQ/Ffxtfqc6ep7KY5TcePE+p41vPImp5WdPXV/G1tFUadPGK2rClJeX0NV1H4g1F6fiWOdk1idj8l+GK8l+80pk09TsnCtYTnJRTk8RTbxlv0LkTlXAG76n8K63TR3yrjbXjO+iXiLHrjCf+hpBqZgQoKAIUAAAAAAAAAAAAAAgKALCG54XfyWG236L3OxqdLfpZxVtc6ptKcVLzXqjBVNxkpLummbzrXUnqatPGa3Srba9ljsRZGO/qluojUrXlQxs4835mz6XqFCyMliW1rCfOTRztw9uVteHlJZx/set+FIaevc7YOblBz34T8NRecLPZszXWNj174kt1FmlqniMNPOXhSqrq+V4Sy2uMrD/aemVcKtJG5pqazJzTzLLfdx7M826NG4LUyrsTlOTsjFZqqeGvr2Zh1HWISlFaack1Haofag1/Aithr/AIxndH9H2OHGPEhzCS94vseU6otPXW64RSj3ynxk760MoKy2+5JyeYwqSak/R57HlutWvd349CxL6auzGXg4AG3AOxGFTjxKcbF64cH9GuV/qdcAbvRfEeqoShvcoLybz6+f5s4Wwr1tsfD2U32N5T+Sqyff/C36+vf1NQE2mmuGmmvZkxrk2/8Ayzr/APt3/m0//QOn42p/Fd/5gqenTKQoAAAAQoAAAAAAAIAKABDJB54bFFUrJRhFZlJ4Xp9WZ4RjCCbXzTXf8KIsZ+maXxrYx/az6HpPBq07qilltb5cfkv3v8j5107Uuu1S5flhG+1PUGtrnFRco5iuzb91kzY6eNxtPiXrCpXhUOPzpbku2PTB5yi2MGpStlTnmTgsy+i9GY5WtvO3dNvjLN3pelR8B2WxTlJNvK4/L2Hw+tLqviK+17Z2ytgn8rnjdjyzg1F9jnJv1MnUNqskorCTOsakc7aHNIkUcisuLRMHIAcAcsEwBn/Spfis/wA2QOuAKAAoAAAAAAAAAAAAAgKd7pWkVkt81J1VygmkvtzeWq89llRly/QDYw6XLT6Si6SmrtbvlCK3KVWljhxsaxxuklz+HD+8s9SzW7vmlz8soYjWsbWvt+zzny4wfXvg/wCCK9botZ+m3SjF1uPiwk63pbIYacecbYrdlPvn6M+U6/S+FLU1R1FWojp7FXG2NTjXdXKXE9ko5TTTyn6Pl8ZiutXLxE5SfzYioxi5KpNqTTlHHZ4iu/nz7c9NbTicp7pWJNtpvEl6uWGufTg7tHSp7nhwqtUbZJTg5VS25i+VlJZzjHHC9ka6+vMUtkKrFmLUJZwk2tvs+Hxl9/cGt70PqOkTSzGFvO1XbYQXvu8/ouWdPrXxDOblCEt0eykliP1R52yL4z+3Hf8AicRhzuDeXlnJIJFKypAAIDNpNLbfPw6oOyey2zasZ2V1ysm+fSMZP8js1dE1k9u3Tze6zTVR5gszvqdtK5f3oJyz6AdAh3pdI1SjGTpklOivUwy4ZnRZb4UJxWctObUeDBrNHbRJRtg65PfhPH3LJVy7ekoSX5AYCFIFUAAAAAAAAAAAAAAM+lphKX6yThCPMsLMn7L0+oGDB7fodOno6evHhG6vUuUnW521LcuNzcGpcbku/wB198nlL761PFa/VrGE13OHiyimtz2Se6L9HlMlJcfY/h74zst0XUdLKUI7a5W/pFajXN17XF1uL7vEU1NfiXGFl/IbNZZHhWRxB4Sl80nmLz5Y/b7HXq1Lipx+7NLKwll4aT/ZKRiqm4NSWMxfGVkGtxDqVzg1esprMWmqZyXCcW48rK88duOzRrNW257tihujFpLs/lWWmv8AY4Z5XzY+9nGWnnnPb6+ff3Zx3vlL7L8n6eQQ3See7z37sJfz7nEqXr6cfz9CjkCAAAAPoP8ARN06rUPWOelhqZxu6ZWt1e916ezUOOqePJOlWJn0TS9BjmGNFwoa+7e9Nsas00qqtLFfKuYxtsjB99tXGeW/gfTNWtPfC51V3qCmnVak657oOPzLHK5z+Rs18RQTjJdP0SlFLD8OPOOIv7Pol+fPsQfZuofD9aWKdE3OEesUwl+iYjCFKlZpFFuviMbFXtTTUnn7eFI81/Sf0WFXSI6mVEIWyu6c4vwtk6526eyepWcfesWX7nzzS/EEKqY1f8P0M5KLi7Z1Rc38kI98f2W/PmUvU6PVOoLUOGKKaFBf9KKTl+rrhmWEst+G5N+s5AdEAFVSAAAABSAAUEAFBAB2+l/1q+jMGo7r6AAYzM/6v/EgAjCEABCgAGcp91/dh/6IACFIAKQAAAABAAoAAj//2Q==', 'tokens':'9'},
    {'name':'God Did ', 'url':'', 'description':' DJ Khalid', 'uri':'https://upload.wikimedia.org/wikipedia/en/0/0a/DJ_Khaled_-_God_Did.png', 'tokens':'10'},
    {'name':'Badtameez Dil', 'url':'', 'description':' Yeh Jawaani Hai Deewani', 'uri':'https://m.media-amazon.com/images/M/MV5BNWIxZWU1YzAtYTc4NS00NTM4LWJmODgtYzEwNTE0NmJiYzI4XkEyXkFqcGdeQXVyODk2ODI3MTU@._V1_UX200_CR0,0,200,200_AL_.jpg', 'tokens':'11'},
    {'name':'Same Old Love', 'url':'', 'description':' Selena Gomez', 'uri':'https://upload.wikimedia.org/wikipedia/en/b/b3/Same_Old_Love_by_Selena_Gomez.png', 'tokens':'12'},
    {'name':'Waka Waka ', 'url':'', 'description':' Shakira', 'uri':'https://photos.prnewswire.com/prnfull/20100901/NY58538-a', 'tokens':'13'},
    {'name':'Swim', 'url':'', 'description':' Chase Atlantic ', 'uri':'https://i.ytimg.com/vi/ykP640XEjSQ/maxresdefault.jpg', 'tokens':'14'},
    {'name':'Fireside', 'url':'', 'description':' Arctic Monkeys', 'uri':'https://i.ytimg.com/vi/PG8yTUeptFU/maxresdefault.jpg', 'tokens':'15'},
    {'name':'Daddy Issues', 'url':'', 'description':' The Neighborhood', 'uri':'https://i.scdn.co/image/ab67616d0000b2733066581d697fbdee4303d685', 'tokens':'16'},
    {'name':'Art Deco', 'url':'', 'description':'Lana Del Rey ', 'uri':'https://i1.sndcdn.com/artworks-000144834419-kkxrj8-t500x500.jpg', 'tokens':'17'},
    {'name':'The Color Violet', 'url':'/audios/COLOR.mp3', 'description':' Tory Lanez ', 'uri':'https://i1.sndcdn.com/artworks-XTdw6XGAR3WX-0-t500x500.jpg', 'tokens':'18'},
    {'name':'Light it Up', 'url':'', 'description':' Major Lazer', 'uri':'https://i.ytimg.com/vi/r2LpOUwca94/maxresdefault.jpg', 'tokens':'19'},
    {'name':'Maneater', 'url':'', 'description':' Nelly Furtado ', 'uri':'https://upload.wikimedia.org/wikipedia/en/5/56/Maneater_%28Nelly_Furtado_single_-_cover_art%29.png', 'tokens':'20'},
    {'name':'Dark Horse', 'url':'', 'description':' Katy Perry ', 'uri':'https://static.independent.co.uk/s3fs-public/thumbnails/image/2014/02/26/10/katy-perry-dark-horse-v2.jpg', 'tokens':'21'},
    {'name':'Watch', 'url':'', 'description':' Billie Eilish ', 'uri':'https://thomasbleach.files.wordpress.com/2017/07/billie.jpg', 'tokens':'22'},
    {'name':'Eyes Without Face', 'url':'', 'description':' Billy Idol ', 'uri':'https://i.ytimg.com/vi/e7U1YZNgwnY/maxresdefault.jpg', 'tokens':'23'},
    {'name':'Good Days', 'url':'', 'description':' SZA', 'uri':'https://upload.wikimedia.org/wikipedia/en/7/7c/SZA_-_Good_Days.png', 'tokens':'24'},
    {'name':'sdp interlude', 'url':'', 'description':'Travis Scott ', 'uri':'https://i.scdn.co/image/ab67616d0000b273f54b99bf27cda88f4a7403ce', 'tokens':'25'},
    {'name':'Mary', 'url':'', 'description':' Alex G ', 'uri':'https://i.scdn.co/image/ab67616d0000b273c85ca3b845a922baff3041c7', 'tokens':'26'},
    {'name':'Flashing Lights', 'url':'', 'description':'Kanye West ', 'uri':'https://i.scdn.co/image/ab67616d0000b27326f7f19c7f0381e56156c94a', 'tokens':'27'},
    {'name':'Trust issues', 'url':'', 'description':'Drake', 'uri':'https://i1.sndcdn.com/artworks-QHAz47bKkwaj-0-t500x500.jpg', 'tokens':'28'},
    {'name':'Gods Plan', 'url':'', 'description':'Drake ', 'uri':'https://i.ytimg.com/vi/m1a_GqJf02M/maxresdefault.jpg', 'tokens':'29'},
    {'name':'Time to Pretend', 'url':'', 'description':'MGMT ', 'uri':'https://i.scdn.co/image/ab67616d0000b2738b32b139981e79f2ebe005eb', 'tokens':'30'},
    {'name':'Sensei Wu', 'url':'/audios/WU.mp3', 'description':' Ian Wu Father ', 'uri':'https://m.media-amazon.com/images/I/51Zl1Tdk3YL._AC_UF894,1000_QL80_.jpg', 'tokens':'31'},
    ]

        
        # iterate
        for song_data in songs_data:
            existing_song = Song.query.filter_by(_name=song_data['name']).first()
            # If user exists, print a message and update user data
            if existing_song:
                print(f"User with _uid '{song_data['name']}' already exists. Updating user data.")
                existing_song.update(
                    name=song_data['name'],
                    url=song_data['url'],
                    uri=song_data['uri'],
                )
                # If user does not exist, create a new user and add to the database
            else:
                new_song = Song(
                    name=song_data['name'],
                    url=song_data['url'],
                    description=song_data['description'],
                    uri=song_data['uri'],
                    tokens=song_data['tokens']   
                )
                db.session.add(new_song)
        db.session.commit()
        
        
if __name__ == "__main__":
    initSongs()

        </code>
        </pre>
    </section>
    <!-- Lists and Dictionaries Section -->
    <section>
        <h2>Lists and Dictionaries and API </h2>
        <p>In the backend code for my Spotify project, I created a dictionary to store song information. I then iterated through the dictionary and manipulated the data to enhance my coding experience.</p>
        <p>Example of Debugger</p>
        <iframe src="https://drive.google.com/file/d/1FQE1_xs174eiGK2R4xRuCoEaGHLIVShb/preview" width="640" height="480" allow="autoplay"></iframe>

        <iframe src="https://drive.google.com/file/d/1RGZdkD-iPOzXGyXG-QG5_XhsLweuEt7D/preview" width="640" height="480" allow="autoplay"></iframe>
        <pre>
        <code class="javascript">
            [
  {
    "_description": "Travis Scott_",
    "_name": "FEIN",
    "_tokens": 1,
    "_uri": "data:image/jpeg;base64,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",
    "id": 1,
    "url": "/audios/FEIN.mp3"
  },
  {
    "_description": "The Weeknd",
    "_name": "Creepin",
    "_tokens": 2,
    "_uri": "https://i1.sndcdn.com/artworks-sWl8wb2Zk1xthx3m-39RYRQ-t500x500.jpg",
    "id": 2,
    "url": "/audios/CREEP.mp3"
  },
  {
    "_description": " Brent Fiaiyaz",
    "_name": "Role Model",
    "_tokens": 4,
    "_uri": "https://i1.sndcdn.com/artworks-O2SRR9SCgyRq4u4v-eAojjA-t500x500.jpg",
    "id": 3,
    "url": ""
  },
  {
    "_description": " Bryson Tiller",
    "_name": "Right my Wrongs",
    "_tokens": 5,
    "_uri": "https://i.scdn.co/image/ab67616d0000b273d5f3cea8affdca01a0dc754f",
    "id": 4,
    "url": ""
  },
  {
    "_description": " Katy Perry",
    "_name": "Roar",
    "_tokens": 6,
    "_uri": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT_Y92S1N976xSO57PbyPinyoJ8IVnqGPFhLQ&usqp=CAU",
    "id": 5,
    "url": ""
  },
  {
    "_description": " Taylor Swift",
    "_name": "Shake it Off",
    "_tokens": 9,
    "_uri": "https://pyxis.nymag.com/v1/imgs/2d9/6f5/3f8dbd63613637b7843e4653ff548503b9-tay--.w710.jpg",
    "id": 6,
    "url": "/audios/SHAKE.mp3"
  },
  {
    "_description": " The Weeknd_",
    "_name": "Often",
    "_tokens": 8,
    "_uri": "https://cdns-images.dzcdn.net/images/cover/eea9f7fc913300e40307a0ff70dc73cf/350x350.jpg",
    "id": 7,
    "url": "/audios/OFTEN.mp3"
  },
  {
    "_description": " Travis Scott",
    "_name": "Thank God",
    "_tokens": 9,
    "_uri": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBw0NDQ0NDg0NDQ0NDQ4NDQ0ODQ8ODQ0OFhEWFhURFRUYHSghGBomGxUVITEhJSkrLi4uFx8zODMwNygtLysBCgoKDg0OFxAQFy0eHR0rKy0rKy0tLS0rKy0rLS0rLS0tLSstLS0tLS0tLS0tLSstLS0rLTctLSstLS0tLSs3K//AABEIAOEA4QMBIgACEQEDEQH/xAAbAAEBAAIDAQAAAAAAAAAAAAAAAQMFAgQGB//EAD0QAAICAQMCBAMEBggHAAAAAAABAgMRBBIhBTETQVFhBiJxMkJSgRQjkbHR8AczYnKCk6HBFRZDVKKy0v/EABcBAQEBAQAAAAAAAAAAAAAAAAABAgP/xAAcEQEBAQACAwEAAAAAAAAAAAAAARESQQIhMVH/2gAMAwEAAhEDEQA/APigAKoAQCgAAAAAAAAACFIUAAQCgEAFAAAAAAAAAAAAAQAAUAAAAAAAAAAAAAAAAhQABAKAQCgAAQoAAAAAAAAAEKQCghQAAAAACFAAAAAAAAIUAAAABAKQoAAEAoIUAAAAAAEKQAUAAAAAAAAAACACghQAIUCFIUAAQCgAAAAAAAAAAAAICkAoAAAgAoAAJZaXm+Ec3Da2pd8eXPOOEcDJuykscrP5r0A4CSDXp+wSA4gAAUhQAAAAEAoAAAEAoAAAAAAABAAKAABCgAAAATBAOQkRdigcQAAKAAIUACFIBQQoAhQAAAAAAAAAAAAAAACAUAAAAARUQBFnHDwcTsWRzFPzRgCoAUCFAAAAACHOFUpdl+5AcQZJaexc7JY9Uty/0MbWAAAAAAAAAABAKAAABAKAAAAAAADs6dpvDLrdK4Ymvsvh+zMUF2PS6fTxvp2v7yaXruRFjyhTnfU65yhLvF4+vuYyooIAKAEAM9M8Psn+RhwZo7oxjJSall9uGkQj6N0XSdKt6LrNRdF06rT027WntjbY44rg49nmTivXk8r1zoNldNN+PmdUd8cNNwUFtl9cLt7GTS9QsuVGjlKM61bC2U+U7IxhKXhyS+1z5900d7qnUvFeyUVFxs3YTeGvtNfXCKWdvFAs0k2o/Zy1H1xnggAAAAAAIABQAAAIBQAAAAAAAc65eXuen6TYo1yk5NJdmucNNM8obPTa3FFkH5uP5Eqyu58U0xbr1EEvmW2zHZPun9HzyaE3fTeobJx3rdDGHF9mv4DrfS4LN+mj+q5c6087P7S/s+3kSVbO2kBAaZUAIAd6DnOEFKUJ7X8sV/WY/B6+/wDLOmln+Jm0stsoyTeV/LIRuug9Unp7swjDMk4fMlJL0f8APuY+oayE77bPklGW5ONblDw+eZ9vxqOO+cGqjZLL29329snO3XWeF+jqX6vc5NJLmWOefJcdg1rpIoBWQG56X8La/V1u2ijdDOE5SUN3GeM9zrdS6FrdJj9I01tSaypOO6GP70comxcrXgAqICkAoIUAAAIUAAAAAAADIAHOFmOPI7vT+pSqeH80fL2NeQmGtp1PRV7FqKJRdcnida+1VL+H7jWxhKWcRlLHfEW8fsOdWolGMo8NTWGn+89b8FdXjiWlsaUZ8QWIpZxwucD41JLXjSnoviHpihfunDw1N+qSk/qY6+kUyinmSbJpwrRJnJT+h6Xqnwo6KYWuUk5pOCltxNN+WHkwaX4VunjduWe2I5LsONaOFmOfPnBl6d06/VWKumuU5N4bS+WPu2e20H9H+F42onJVRTk/lxlL3Z6HSavQ6SpR08q8ecm488epLVnj+tBo/g7Q1vZqVqbZRS8SdcsVwb9ks447njuvUaerVWQ0zlKiMltcpbn784PQ/Ffxtfqc6ep7KY5TcePE+p41vPImp5WdPXV/G1tFUadPGK2rClJeX0NV1H4g1F6fiWOdk1idj8l+GK8l+80pk09TsnCtYTnJRTk8RTbxlv0LkTlXAG76n8K63TR3yrjbXjO+iXiLHrjCf+hpBqZgQoKAIUAAAAAAAAAAAAAAgKALCG54XfyWG236L3OxqdLfpZxVtc6ptKcVLzXqjBVNxkpLummbzrXUnqatPGa3Srba9ljsRZGO/qluojUrXlQxs4835mz6XqFCyMliW1rCfOTRztw9uVteHlJZx/set+FIaevc7YOblBz34T8NRecLPZszXWNj174kt1FmlqniMNPOXhSqrq+V4Sy2uMrD/aemVcKtJG5pqazJzTzLLfdx7M826NG4LUyrsTlOTsjFZqqeGvr2Zh1HWISlFaack1Haofag1/Aithr/AIxndH9H2OHGPEhzCS94vseU6otPXW64RSj3ynxk760MoKy2+5JyeYwqSak/R57HlutWvd349CxL6auzGXg4AG3AOxGFTjxKcbF64cH9GuV/qdcAbvRfEeqoShvcoLybz6+f5s4Wwr1tsfD2U32N5T+Sqyff/C36+vf1NQE2mmuGmmvZkxrk2/8Ayzr/APt3/m0//QOn42p/Fd/5gqenTKQoAAAAQoAAAAAAAIAKABDJB54bFFUrJRhFZlJ4Xp9WZ4RjCCbXzTXf8KIsZ+maXxrYx/az6HpPBq07qilltb5cfkv3v8j5107Uuu1S5flhG+1PUGtrnFRco5iuzb91kzY6eNxtPiXrCpXhUOPzpbku2PTB5yi2MGpStlTnmTgsy+i9GY5WtvO3dNvjLN3pelR8B2WxTlJNvK4/L2Hw+tLqviK+17Z2ytgn8rnjdjyzg1F9jnJv1MnUNqskorCTOsakc7aHNIkUcisuLRMHIAcAcsEwBn/Spfis/wA2QOuAKAAoAAAAAAAAAAAAAgKd7pWkVkt81J1VygmkvtzeWq89llRly/QDYw6XLT6Si6SmrtbvlCK3KVWljhxsaxxuklz+HD+8s9SzW7vmlz8soYjWsbWvt+zzny4wfXvg/wCCK9botZ+m3SjF1uPiwk63pbIYacecbYrdlPvn6M+U6/S+FLU1R1FWojp7FXG2NTjXdXKXE9ko5TTTyn6Pl8ZiutXLxE5SfzYioxi5KpNqTTlHHZ4iu/nz7c9NbTicp7pWJNtpvEl6uWGufTg7tHSp7nhwqtUbZJTg5VS25i+VlJZzjHHC9ka6+vMUtkKrFmLUJZwk2tvs+Hxl9/cGt70PqOkTSzGFvO1XbYQXvu8/ouWdPrXxDOblCEt0eykliP1R52yL4z+3Hf8AicRhzuDeXlnJIJFKypAAIDNpNLbfPw6oOyey2zasZ2V1ysm+fSMZP8js1dE1k9u3Tze6zTVR5gszvqdtK5f3oJyz6AdAh3pdI1SjGTpklOivUwy4ZnRZb4UJxWctObUeDBrNHbRJRtg65PfhPH3LJVy7ekoSX5AYCFIFUAAAAAAAAAAAAAAM+lphKX6yThCPMsLMn7L0+oGDB7fodOno6evHhG6vUuUnW521LcuNzcGpcbku/wB198nlL761PFa/VrGE13OHiyimtz2Se6L9HlMlJcfY/h74zst0XUdLKUI7a5W/pFajXN17XF1uL7vEU1NfiXGFl/IbNZZHhWRxB4Sl80nmLz5Y/b7HXq1Lipx+7NLKwll4aT/ZKRiqm4NSWMxfGVkGtxDqVzg1esprMWmqZyXCcW48rK88duOzRrNW257tihujFpLs/lWWmv8AY4Z5XzY+9nGWnnnPb6+ff3Zx3vlL7L8n6eQQ3See7z37sJfz7nEqXr6cfz9CjkCAAAAPoP8ARN06rUPWOelhqZxu6ZWt1e916ezUOOqePJOlWJn0TS9BjmGNFwoa+7e9Nsas00qqtLFfKuYxtsjB99tXGeW/gfTNWtPfC51V3qCmnVak657oOPzLHK5z+Rs18RQTjJdP0SlFLD8OPOOIv7Pol+fPsQfZuofD9aWKdE3OEesUwl+iYjCFKlZpFFuviMbFXtTTUnn7eFI81/Sf0WFXSI6mVEIWyu6c4vwtk6526eyepWcfesWX7nzzS/EEKqY1f8P0M5KLi7Z1Rc38kI98f2W/PmUvU6PVOoLUOGKKaFBf9KKTl+rrhmWEst+G5N+s5AdEAFVSAAAABSAAUEAFBAB2+l/1q+jMGo7r6AAYzM/6v/EgAjCEABCgAGcp91/dh/6IACFIAKQAAAABAAoAAj//2Q==",
    "id": 8,
    "url": ""
  },
  {
    "_description": " DJ Khalid",
    "_name": "God Did ",
    "_tokens": 10,
    "_uri": "https://upload.wikimedia.org/wikipedia/en/0/0a/DJ_Khaled_-_God_Did.png",
    "id": 9,
    "url": ""
  },
  {
    "_description": " Yeh Jawaani Hai Deewani",
    "_name": "Badtameez Dil",
    "_tokens": 11,
    "_uri": "https://m.media-amazon.com/images/M/MV5BNWIxZWU1YzAtYTc4NS00NTM4LWJmODgtYzEwNTE0NmJiYzI4XkEyXkFqcGdeQXVyODk2ODI3MTU@._V1_UX200_CR0,0,200,200_AL_.jpg",
    "id": 10,
    "url": ""
  },
  {
    "_description": " Selena Gomez",
    "_name": "Same Old Love",
    "_tokens": 12,
    "_uri": "https://upload.wikimedia.org/wikipedia/en/b/b3/Same_Old_Love_by_Selena_Gomez.png",
    "id": 11,
    "url": ""
  },
  {
    "_description": " Shakira",
    "_name": "Waka Waka ",
    "_tokens": 13,
    "_uri": "https://photos.prnewswire.com/prnfull/20100901/NY58538-a",
    "id": 12,
    "url": ""
  },
  {
    "_description": " Chase Atlantic ",
    "_name": "Swim",
    "_tokens": 14,
    "_uri": "https://i.ytimg.com/vi/ykP640XEjSQ/maxresdefault.jpg",
    "id": 13,
    "url": ""
  },
  {
    "_description": " Arctic Monkeys",
    "_name": "Fireside",
    "_tokens": 15,
    "_uri": "https://i.ytimg.com/vi/PG8yTUeptFU/maxresdefault.jpg",
    "id": 14,
    "url": ""
  },
  {
    "_description": " The Neighborhood",
    "_name": "Daddy Issues",
    "_tokens": 16,
    "_uri": "https://i.scdn.co/image/ab67616d0000b2733066581d697fbdee4303d685",
    "id": 15,
    "url": ""
  },
  {
    "_description": "Lana Del Rey ",
    "_name": "Art Deco",
    "_tokens": 17,
    "_uri": "https://i1.sndcdn.com/artworks-000144834419-kkxrj8-t500x500.jpg",
    "id": 16,
    "url": ""
  },
  {
    "_description": " Tory Lanez ",
    "_name": "The Color Violet",
    "_tokens": 18,
    "_uri": "https://i1.sndcdn.com/artworks-XTdw6XGAR3WX-0-t500x500.jpg",
    "id": 17,
    "url": "/audios/COLOR.mp3"
  },
  {
    "_description": " Major Lazer",
    "_name": "Light it Up",
    "_tokens": 19,
    "_uri": "https://i.ytimg.com/vi/r2LpOUwca94/maxresdefault.jpg",
    "id": 18,
    "url": ""
  },
  {
    "_description": " Nelly Furtado ",
    "_name": "Maneater",
    "_tokens": 20,
    "_uri": "https://upload.wikimedia.org/wikipedia/en/5/56/Maneater_%28Nelly_Furtado_single_-_cover_art%29.png",
    "id": 19,
    "url": ""
  },
  {
    "_description": " Katy Perry ",
    "_name": "Dark Horse",
    "_tokens": 21,
    "_uri": "https://static.independent.co.uk/s3fs-public/thumbnails/image/2014/02/26/10/katy-perry-dark-horse-v2.jpg",
    "id": 20,
    "url": ""
  },
  {
    "_description": " Billie Eilish ",
    "_name": "Watch",
    "_tokens": 22,
    "_uri": "https://thomasbleach.files.wordpress.com/2017/07/billie.jpg",
    "id": 21,
    "url": ""
  },
  {
    "_description": " Billy Idol ",
    "_name": "Eyes Without Face",
    "_tokens": 23,
    "_uri": "https://i.ytimg.com/vi/e7U1YZNgwnY/maxresdefault.jpg",
    "id": 22,
    "url": ""
  },
  {
    "_description": " SZA",
    "_name": "Good Days",
    "_tokens": 24,
    "_uri": "https://upload.wikimedia.org/wikipedia/en/7/7c/SZA_-_Good_Days.png",
    "id": 23,
    "url": ""
  },
  {
    "_description": "Travis Scott ",
    "_name": "sdp interlude",
    "_tokens": 25,
    "_uri": "https://i.scdn.co/image/ab67616d0000b273f54b99bf27cda88f4a7403ce",
    "id": 24,
    "url": ""
  },
  {
    "_description": " Alex G ",
    "_name": "Mary",
    "_tokens": 26,
    "_uri": "https://i.scdn.co/image/ab67616d0000b273c85ca3b845a922baff3041c7",
    "id": 25,
    "url": ""
  },
  {
    "_description": "Kanye West ",
    "_name": "Flashing Lights",
    "_tokens": 27,
    "_uri": "https://i.scdn.co/image/ab67616d0000b27326f7f19c7f0381e56156c94a",
    "id": 26,
    "url": ""
  },
  {
    "_description": "Drake",
    "_name": "Trust issues",
    "_tokens": 28,
    "_uri": "https://i1.sndcdn.com/artworks-QHAz47bKkwaj-0-t500x500.jpg",
    "id": 27,
    "url": ""
  },
  {
    "_description": "Drake ",
    "_name": "Gods Plan",
    "_tokens": 29,
    "_uri": "https://i.ytimg.com/vi/m1a_GqJf02M/maxresdefault.jpg",
    "id": 28,
    "url": ""
  },
  {
    "_description": "MGMT ",
    "_name": "Time to Pretend",
    "_tokens": 30,
    "_uri": "https://i.scdn.co/image/ab67616d0000b2738b32b139981e79f2ebe005eb",
    "id": 29,
    "url": ""
  },
  {
    "_description": " Ian Wu Father ",
    "_name": "Sensei Wu",
    "_tokens": 31,
    "_uri": "https://m.media-amazon.com/images/I/51Zl1Tdk3YL._AC_UF894,1000_QL80_.jpg",
    "id": 30,
    "url": "/audios/WU.mp3"
  }
]
        </code>
        </pre>
        <pre>
        <code class = "python">
            from flask import Blueprint, jsonify, request  # Import the 'request' object
from flask_restful import Api, Resource, reqparse
from __init__ import db
from flask_cors import CORS
from model.songs import Song

Song_api = Blueprint('Song_Api', __name__, url_prefix="/api/song")

api = Api(Song_api)

CORS(Song_api)  #

class SongAPI(Resource):
    def post(self):
        parser = reqparse.RequestParser()
        parser.add_argument("_name", type=str, required=True, help="Name is required")
        parser.add_argument("_description", type=str, required=True, help="Description is required")
        parser.add_argument("_uri", type=str, required=True, help="URI is required")
        parser.add_argument("_tokens", type=int, required=True, help="Tokens is required")
        parser.add_argument("_url", type=str, required=True, help="URL is required")  # Add URL argument
        args = parser.parse_args()

        new_song = Song(_name=args["_name"], _description=args["_description"], _uri=args["_uri"], _tokens=args["_tokens"], _url=args["_url"])
        db.session.add(new_song)
        db.session.commit()

        return jsonify(new_song.to_dict()), 201
    
    def get(self, song_id=None):  # Add song_id as a parameter with a default value of None
        if song_id is not None:
            song = Song.query.get(song_id)
            if song:
                return jsonify(song.to_dict())
            return {"error": "Song not found"}, 404

        # Handle the case when no song_id is provided, e.g., for the "/all" endpoint
        songs = Song.query.all()
        songs_data = [song.to_dict() for song in songs]
        return jsonify(songs_data)
    
    def put(self, song_id):
        song = Song.query.get(song_id)
        if not song:
            return {"error": "Song not found"}, 404

        parser = reqparse.RequestParser()
        parser.add_argument("_name", type=str)
        parser.add_argument("_description", type=str)
        parser.add_argument("_uri", type=str)
        parser.add_argument("_tokens", type=int)
        args = parser.parse_args()

        if args["_name"]:
            song._name = args["_name"]
        if args["_description"]:
            song._description = args["_description"]
        if args["_uri"]:
            song._uri = args["_uri"]
        if args["_tokens"]:
            song._tokens = args["_tokens"]

        db.session.commit()

        return jsonify(song.to_dict())

    def delete(self, song_id):
        song = Song.query.get(song_id)
        if not song:
            return {"error": "Song not found"}, 404

        db.session.delete(song)
        db.session.commit()

        return {"message": "Song deleted successfully"}, 200
    
    def create_song(self):  # Move the 'create_song' method inside the class
        data = request.json  # Use 'request' object from Flask
        name = data.get('_name')
        description = data.get('_description')
        uri = data.get('_uri')
        tokens = data.get('_tokens')
        url = data.get('_url')

        new_song = Song(_name=name, _description=description, _uri=uri, _tokens=tokens, _url=url)
        db.session.add(new_song)
        db.session.commit()

        return jsonify(new_song.to_dict()), 201

        </code>
        </pre>
    </section>
    <!-- APIs and JSON Section -->
    <section>
        <h2>APIs and JSON</h2>
        <p>In the Spotify clone project, I developed APIs to interact with the database. The GET method retrieves songs from the database, while the POST/UPDATE methods allow for adding and modifying song data.</p>
        <p>To handle various HTTP requests in the API, I've defined different methods within the `SongAPI` class. Each method corresponds to a different HTTP request method: `post`, `get`, `put`, and `delete`. The Flask-Restful library automatically routes incoming requests to the appropriate method based on the HTTP method used in the request. For example, `POST` requests are directed to the `post` method, `GET` requests to the `get` method, and so on. This routing logic eliminates the need for explicit conditionals to direct requests to the correct method.</p>
<iframe src="https://drive.google.com/file/d/1i0TyDfA3mGTW_U5jRvOKquUZv23TgjGj/preview" width="640" height="480" allow="autoplay"></iframe>
<iframe src="https://drive.google.com/file/d/1mT9-J4p90nbGneO5jGTb6uIQHuLUx7ke/preview" width="640" height="480" allow="autoplay"></iframe>
<iframe src="https://drive.google.com/file/d/1ME6h6o-tDZV6Jh_6NWq4RuPAqYe_JrwM/preview" width="640" height="480" allow="autoplay"></iframe>
<iframe src="https://drive.google.com/file/d/1RH8QkwsRHEz-gbLwTuJSbdzfutRhIQRg/preview" width="640" height="480" allow="autoplay"></iframe>

<pre>
<code class="python">
from flask import Blueprint, jsonify, request
from flask_restful import Api, Resource, reqparse
from __init__ import db
from flask_cors import CORS
from model.songs import Song

Song_api = Blueprint('Song_Api', __name__, url_prefix="/api/song")
api = Api(Song_api)
CORS(Song_api)

def post(self):
        parser = reqparse.RequestParser()
        parser.add_argument("_name", type=str, required=True, help="Name is required")
        parser.add_argument("_description", type=str, required=True, help="Description is required")
        parser.add_argument("_uri", type=str, required=True, help="URI is required")
        parser.add_argument("_tokens", type=int, required=True, help="Tokens is required")
        parser.add_argument("_url", type=str, required=True, help="URL is required")  # Add URL argument
        args = parser.parse_args()

        new_song = Song(_name=args["_name"], _description=args["_description"], _uri=args["_uri"], _tokens=args["_tokens"], _url=args["_url"])
        db.session.add(new_song)
        db.session.commit()

        return jsonify(new_song.to_dict()), 201
    
    def get(self, song_id=None):  # Add song_id as a parameter with a default value of None
        if song_id is not None:
            song = Song.query.get(song_id)
            if song:
                return jsonify(song.to_dict())
            return {"error": "Song not found"}, 404

        # Handle the case when no song_id is provided, e.g., for the "/all" endpoint
        songs = Song.query.all()
        songs_data = [song.to_dict() for song in songs]
        return jsonify(songs_data)
    
    def put(self, song_id):
        song = Song.query.get(song_id)
        if not song:
            return {"error": "Song not found"}, 404

        parser = reqparse.RequestParser()
        parser.add_argument("_name", type=str)
        parser.add_argument("_description", type=str)
        parser.add_argument("_uri", type=str)
        parser.add_argument("_tokens", type=int)
        args = parser.parse_args()

        if args["_name"]:
            song._name = args["_name"]
        if args["_description"]:
            song._description = args["_description"]
        if args["_uri"]:
            song._uri = args["_uri"]
        if args["_tokens"]:
            song._tokens = args["_tokens"]

        db.session.commit()

        return jsonify(song.to_dict())

    def delete(self, song_id):
        song = Song.query.get(song_id)
        if not song:
            return {"error": "Song not found"}, 404

        db.session.delete(song)
        db.session.commit()

        return {"message": "Song deleted successfully"}, 200
    
    def create_song(self):  # Move the 'create_song' method inside the class
        data = request.json  # Use 'request' object from Flask
        name = data.get('_name')
        description = data.get('_description')
        uri = data.get('_uri')
        tokens = data.get('_tokens')
        url = data.get('_url')

        new_song = Song(_name=name, _description=description, _uri=uri, _tokens=tokens, _url=url)
        db.session.add(new_song)
        db.session.commit()

        return jsonify(new_song.to_dict()), 201

</code>
</pre>

<p>In the `post` method, I've used the `reqparse.RequestParser()` object to parse and validate the request data. Each argument added to the parser specifies the type and requirements for the data. For instance, `required=True` ensures that the argument is present in the request, and `help="Name is required"` provides an error message if the argument is missing. Additionally, conditional checks are used to validate and update the song data based on the provided arguments.</p>

<pre>
<code class="python">
    def post(self):
        parser = reqparse.RequestParser()
        parser.add_argument("_name", type=str, required=True, help="Name is required")
        parser.add_argument("_description", type=str, required=True, help="Description is required")
        parser.add_argument("_uri", type=str, required=True, help="URI is required")
        parser.add_argument("_tokens", type=int, required=True, help="Tokens is required")
        parser.add_argument("_url", type=str, required=True, help="URL is required")
        args = parser.parse_args()

        new_song = Song(_name=args["_name"], _description=args["_description"], _uri=args["_uri"], _tokens=args["_tokens"], _url=args["_url"])
        db.session.add(new_song)
        db.session.commit()

        return jsonify(new_song.to_dict()), 201
</code>
</pre>
    </section>
    <!-- Frontend Section -->
    <section>
        <h2>Frontend</h2>
        <p>To create a seamless user experience, I integrated all of my projects into a single window-like interface. Here's how the frontend code looks:</p>
        <pre><code class="typescript">let currentSongUrl = null; // Track the current song URL
    let audio = null; // Track the audio element

    function redirectToSongPageContainer(event) {
        // Get the target element that was clicked
        const clickedElement = event.target;

        // Check if the clicked element is the play button
        if (clickedElement.classList.contains("fa-play")) {
            // Get the closest item container
            const item = clickedElement.closest(".item");
            // Get the song URL from the dataset
            const songUrl = item.dataset.songUrl;

            // You can store the song URL here or perform any other action

            // Prevent the default action of playing the song
            event.preventDefault();
        }
    }


      // Load data when the page is loaded
      window.onload = function () {
          fetchData();
          document.getElementById("albumList").addEventListener("click", redirectToSongPageContainer);
          const playButton = document.getElementById("playButton");
          playButton.addEventListener("click", togglePlayPause);
      };

      function createItemBlock(data) {
          const item = document.createElement("div");
          item.classList.add("item");
      
          // Assuming your data structure has changed
          const img = document.createElement("img");
          img.src = data._uri; // Update this to match your actual URI field
          item.appendChild(img);
      
          const play = document.createElement("div");
          play.classList.add("play");
          const playIcon = document.createElement("span");
          playIcon.classList.add("fa", "fa-play");
          playIcon.addEventListener("click", () => {
              // Store the song URL in sessionStorage
              sessionStorage.setItem('currentSongUrl', data.url);
              // Play the song
              playSong(data.url);
              // Update the now playing text
              const nowPlaying = document.getElementById('nowPlaying');
              nowPlaying.textContent = `Now Playing: ${data._name}`;
          });
          play.appendChild(playIcon);
          item.appendChild(play);
      
          // Set the song name in the dataset
          item.dataset.songName = data._name;
          // Set the song URL in the dataset
          item.dataset.songUrl = data.url;
      
          const h4 = document.createElement("h4");
          h4.textContent = data._name; // Update this to match your actual name field
          item.appendChild(h4);
      
          const p = document.createElement("p");
          p.textContent = data._description; // Update this to match your actual tokens field
          item.appendChild(p);
      
          return item;
      }

      // Fetch data from Flask backend
      async function fetchData() {
          try {
              const response = await fetch('http://127.0.0.1:8086/api/song/all');
              const songsData = await response.json();
      
              const container = document.getElementById("albumList");
      
              // Map through the list and create song cards
              songsData.forEach((song) => {
                  const itemBlock = createItemBlock(song);
                  container.appendChild(itemBlock);
              });
          } catch (error) {
              console.error('Error fetching data:', error);
          }
      }

      function playSong(songUrl) {
          // Pause the currently playing audio if any
          if (audio) {
              audio.pause();
          }

          // Create a new audio element and play the song
          audio = new Audio(songUrl);
          audio.play();
      }

      function togglePlayPause() {
          // If audio is paused, play it, and vice versa
          if (audio.paused) {
              audio.play();
              this.textContent = 'Pause';
          } else {
              audio.pause();
              this.textContent = 'Play';
          }
      }
</code></pre>
    </section>
    <!-- Machine Learning Section -->
    <section>
        <h2>Machine Learning</h2>
        <p>For the image classification project using PyTorch, I implemented a ResNet model. Here's a snippet of the code:</p>
        <pre><code class="python">
        import os
import torch
import torch.nn as nn
import torch.optim as optim
from torchvision import datasets, models, transforms
from torch.utils.data import DataLoader
from collections import Counter
from PIL import Image
from io import BytesIO

class ImageClassifier:
    _instance = None

    def __new__(cls, dataset_path=None, img_width=128, img_height=128, batch_size=32):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
            cls._instance.dataset_path = dataset_path
            cls._instance.img_width = img_width
            cls._instance.img_height = img_height
            cls._instance.batch_size = batch_size

            # Initialize variables
            cls._instance.data_transforms = transforms.Compose([
                transforms.Resize((cls._instance.img_width, cls._instance.img_height)),
                transforms.CenterCrop(cls._instance.img_width),
                transforms.ToTensor(),
                transforms.Normalize([0.485, 0.456, 0.406], [0.229, 0.224, 0.225])
            ])

            cls._instance.label_vocab = None
            cls._instance.image_dataset = None
            cls._instance.data_loader = None
            cls._instance.model = None

            cls._instance._preprocess_data()
            cls._instance._initialize_model()

        return cls._instance

    def _preprocess_data(self):
        images = []
        labels = []
        max_images_per_place = 12
        for location_folder in os.listdir(self.dataset_path):
            location_folder_path = os.path.join(self.dataset_path, location_folder)
            if os.path.isdir(location_folder_path):
                count = 0
                for image_file in os.listdir(location_folder_path):
                    if count >= max_images_per_place:
                        break
                    image_path = os.path.join(location_folder_path, image_file)
                    image = self.data_transforms(Image.open(image_path))
                    images.append(image)
                    labels.append(location_folder)
                    count += 1

        label_counter = Counter(labels)
        self.label_vocab = {label: i for i, label in enumerate(label_counter)}
        labels = [self.label_vocab[label] for label in labels]

        images = torch.stack(images)
        labels = torch.tensor(labels)

        self.image_dataset = torch.utils.data.TensorDataset(images, labels)
        self.data_loader = DataLoader(self.image_dataset, batch_size=self.batch_size, shuffle=True)

    def _initialize_model(self):
        num_classes = len(self.label_vocab)
        self.model = models.resnet50(pretrained=True)
        num_features = self.model.fc.in_features
        self.model.fc = nn.Linear(num_features, num_classes)

    def train_model(self, num_epochs=10):
        criterion = nn.CrossEntropyLoss()
        optimizer = optim.SGD(self.model.parameters(), lr=0.001, momentum=0.9)

        self.model.train()
        for epoch in range(num_epochs):
            running_loss = 0.0
            for inputs, labels in self.data_loader:
                optimizer.zero_grad()
                outputs = self.model(inputs)
                loss = criterion(outputs, labels)
                loss.backward()
                optimizer.step()
                running_loss += loss.item() * inputs.size(0)
            epoch_loss = running_loss / len(self.image_dataset)
            print(f"Epoch {epoch+1}/{num_epochs}, Loss: {epoch_loss:.4f}")

    def predict_image_class(self, image):
        image = self.data_transforms(image).unsqueeze(0)
        self.model.eval()
        with torch.no_grad():
            output = self.model(image)
            _, predicted = torch.max(output, 1)
            predicted_item = predicted.item()
            return predicted_item

def initPlaces():
    global places_classifier
    places_classifier = ImageClassifier(dataset_path='./places')

# Call the initialization function


# classifier = ImageClassifier(dataset_path='/Users/shubhay/Documents/GitHub/BackendTri3/places')
# classifier.train_model()
# predicted_class = classifier.predict_image_class("/content/drive/MyDrive/ML/Data/places/Golden_Gate_Bridge/00b4e41b02.jpg")
# print("Predicted class:", predicted_class)

        </code></pre>
    </section>
</body>
</html>
