# hangmaninpython

#Establish the data set for the computer's dictionary
#better to import but not using online libraries for now as they can disappear or be moved
dictionary = ['tinamou','ostrich','rhea','cassowary','emu','kiwi','megapode','chachalaca','curassow','guan','guineafowl',
              'quail','pheasant','fowl','screamer','magpie','goose','duck','geese','swan','loon','penguin','albatross',
              'petrel','shearwater','grebe','flamingo','tropicbird','stork','ibis','spoonbill','heron','bittern','hamerkop',
              'shoebill','pelican','frigatebird','gannet','booby','cormorant','shag','anhinga','darter','vulture',
              'secretarybird','osprey','kite','Hawk','eagle','caracara','falcon','bustard','mesite','seriema','kagu',
              'sunbittern','flufftail','finfoot','rail','crake','coot','trumpeter','crane','limpkin','buttonquail',
              'stonecurlew','thickknees','sheathbill','plover','oystercatcher','ibisbill','stilt','avocet','snipe','jacana',
              'plainswanderer','sandpiper','courser','pratincole','gull','tern','skimmer','skua','auk','sandgrouse','pigeon',
              'dove','parrot','cockatoo','hoatzin','turaco','cuckoo','barnowl','owl','frogmouth','oilbird','potoo','nightjar',
              'treeswift','swift','hummingbird','mousebird','trogon','roller','kingfisher','tody','motmot','beeeater','hoopoe',
              'hornbill','jacamar','puffbird','barbet','toucan','honeyguide','woodpecker','wren','broadbill','pitta','ovenbird',
              'antbird','antthrush','antpitta','gnateater','tapaculo','crescentchest','flycatcher','cotinga','manakin','tityra',
              'becard','lyrebird','scrubbird','bowerbird','treecreeper','honeyeater','bristlebird','pardalote','logrunner',
              'satinbird','berrypecker','longbill','wattlebird','stitchbird','whipbird','wattleeye','batise','woodshrike',
              'helmetshrike','bushshrike','boatbill','vanga','butcherbird','bristlehead','woodswallow','iora','cuckooshrike',
              'sittella','whistler','shrike','vireo','greenlet','figbird','oriole','drongo','fantail','monarch','crow','jay','mudnester',
              'birdsofparadise','robin','rockfowl','rockjumper','waxwing','hypocolius','palmchat','hylocitrea','tit','chickadee',
              'reedling','nicator','lark','bulbul','martin','babbler','crombec','warbler','bushtit','grassbird','donacobius',
              'laughingthrushes','thrush','cisticola','parrotbill','myzornis','sugarbirds','bluebirds','kinglet','goldcrest','hyliota',
              'gnatcatcher','nuthatch','wallcreeper','mockingbird','thrasher','starling','rhabdornis','oxpecker','dipper','leafbird',
              'flowerpecker','sunbird','snowfinch','weaver','widowbird','waxbill','munia','whydah','indigobird','accentor','wagtail',
              'pipit','finch','oropendola','blackbird','bananaquit','bunting','tanager','longspur','grosbeak','saltator']


#User is asked to guess a word from a certain subject area of the dictionary
print("Guess a bird to begin the game.The length of the name will be my number guesses")
user_word = (input("Which bird are we guessing? Enter here"))

max_attempts = int(input("How long is your word? Enter here"))

#Computer shortlists the words based on length 
def by_size(words,size):
    result = []
    for word in words:
        if len(word)==size:
            result.append(word)
    return result

New_dictionary = by_size(dictionary,max_attempts)
#print(New_dictionary)

#Additional check to pick one random word from shortlisted list and separate them into unique letters
import random
System_guess = random.choice(New_dictionary)
print(System_guess)

def StringConversion(l):
    string1 = " "
    return (string1.join(l)) 
 
ns = (StringConversion(System_guess))
#print("This is the new string",ns)

def removeDuplicate(str, n): 
    counter = 0 
    for i in range(0, n): 
        for j in range(0, i + 1): 
            if (str[i] == str[j]): 
                break

        if (j == i): 
            str[counter] = str[i] 
            counter += 1
              
    return "".join(str[:counter]) 

nosp = ns.replace(" ", "")
us= removeDuplicate(list(nosp),len(nosp))

#print("This is the unique letters of similar legnth",us)

#Computer starts guessing from list of unique letters and through each iteration, abstains from usedletters

Turn = 0
usedletters = []
while True:
    for my_guess in us:
        if my_guess not in usedletters:
            if my_guess in user_word:
                print("I guessed",my_guess,"which is in your word")
            
            else:
                Turn += 1
                print("I guessed",my_guess,"which is a wrong attempt: %d" % Turn)

                Turn == max_attempts
                print("I'm done with my attempts")
                print("Sorry, I lost")
                usedletters.append(my_guess)
    break
                    
                

while Turn == 0:
    if System_guess == user_word:
        print ("I won! I guessed the word",System_guess)
        break
    else:
        print("Sorry, I lost")
        break
