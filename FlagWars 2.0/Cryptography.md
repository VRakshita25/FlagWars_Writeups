# 1. Collide Me If You Can

## Desc:

    >`Author : st3g0`
    
    A legacy authentication system still uses **MD5** to verify file integrity.
    
    The system verifies files by checking:
    MD5(uploaded_file) == stored_MD5
    
    Your job?
    
    Create a **different file with the same MD5 hash** as verified.bin (attached in the website)
    When you upload a colliding file, the system reveals the flag.
    Upload the file here-> https://collide-1.onrender.com


## Soln:

    The system verifies files by checking:
    MD5(uploaded_file) == stored_MD5
    
    Create a **different file with the same MD5 hash** as verified.bin (attached in the website)
    When you upload a colliding file, the system reveals the flag.

    Example working file:  https://drive.google.com/file/d/1vrACSjwukaDxyJ5tQ2Xcw1ydZk01UQXd/view?usp=sharing

## Flag:

    flagwars{md5_collision_master}





# 2. Calm Down

## Desc:

    > `Author : st3g0`
    
    Someone intercepted a suspicious encoded message. 
    https://drive.google.com/drive/folders/1n0P4ml0EwUt1Sptp-ueUrQkiWd9b7e9u?usp=sharing
    
    Attached to it was a crumpled note that just said:
     
    "baby calm down, calm down - **the key** is how many times he says 'calm down' in the chorus. (it's not 4. it's not 2. calm down and count.)"
    
    The message looks like gibberish — or does it? **The first half of the flag is buried inside**.
    
    But that's only half the story. The sender also left behind an official song credits PDF. Nothing suspicious about it. Just a normal credits sheet. Totally normal.
    
    ...**look at who's featuring**. carefully.


## Soln:

    STEP 1 — Caesar Cipher (challenge.txt)
    Ciphertext received:
    fdop grzq, fdop grzq
    edeb, edeb, edeb...
    wkh iluvw kdoi ri zkdw brx vhhn lv klgghq khuh:
    iodjzduv{fdop_grzq_
    
    Caesar shift = 3
    (Rema says "calm down" 3 times in the chorus)
    
    Decrypted:
    igrs juct, igrs juct
    hghe, hghe, hghe...
    znk loxyz ngrl ul cngz eua ykkq oy nojjkt nkxk:
    lrgmcgxy{igrs_juct_
    
    First half of flag: flagwars{calm_down_
    
    STEP 2 — PDF Initials (song_credits.pdf)
    Read FIRST LETTER of each artist in "ADDITIONAL FEATURING ARTISTS":
    
      Ivan Turner-Smith     → I
      Tems                  → T
      Sia Konstantinidis    → S
      Juice WRLD Estate     → J
      Usher Raymond         → U
      Summer Walker         → S
      Ty Dolla $ign         → T
      Chris Nolan-Beats     → C
      Raye                  → R
      Young Jonn            → Y
      Patoranking           → P
      Tekno Miles           → T
      Omah Lay              → O
    
    Initials: i t s j u s t c r y p t o
    With underscores + closing brace: its_just_crypto}
    
    Second half of flag: its_just_crypto}
    
    COMBINE
    flagwars{calm_down_ + its_just_crypto} = flagwars{calm_down_its_just_crypto}


## Flag:

    flagwars{calm_down_its_just_crypto}


# 3. Sixty-four Secrets

## Desc:

    >`Author : EnCase`
    
    When the investigation team raided the apartment, they didn’t find much.

    No notebooks.
    No USB drives.
    No suspicious software.

    Just a single text file open on the screen.

    It wasn’t readable.
    It wasn’t encrypted either — at least not in any way the forensic tools recognized.

    Just a long string of strange characters:

    Uppercase.
    Lowercase.
    Numbers.
    A couple of symbols at the end.

    The analyst smirked.

    “Not everything that looks secure is complicated,” she said.

    Sixty-four characters.
    That’s all it takes to hide a secret.

    Can you uncover what they tried so hard to conceal?

    ZmxhZ3dhcnN7YjRzZTY0X3VuNzBjazNkIX0=

## Soln:

    Go to cyberchef and use the From Base64 recipe.

## Flag:

    flagwars{b4se64_un70ck3d!}

# 4. 1337

## Desc:

    >`Author : EnCase`
    
    It looks readable… but only if you speak 1337.

    Can you translate the code and recover the flag?
    /=[_@6vv/-\25|/4|V1_/‾)-(3|)|]|]
    NOTE: THE FLAG SHOULD BE SUBMITTED IN LOWER CASE

## Soln:

    Go to dCode and use leetspeak decoder

## Flag:

    flagwars{v4n1sh3ddd}



# 5. The Archivist's Mark

## Desc:

    > `Author : st3g0`
    
    **Flag format:** `flagwars{...}`
    
    An anonymous archivist stored their secrets not in words, not in numbers—  
    but in **symbols no human language uses**.
    
    You have recovered a fragment of this encoded script.  
    It is clearly not Base64, not Morse, not Unicode, not classical substitution.
    https://drive.google.com/file/d/1ZY3q044H8duqHgJX1z9ERtV0UZo9WXM6/view?usp=sharing
    
    The symbols seem to follow a strict positional pattern.  
    But the message is additionally wrapped in an unfamiliar percent-encoded layer.
    
    Decrypt the archive and recover the flag.


## Soln:

    import urllib.parse
    
    ALPHABET = 'abcdefghijklmnopqrstuvwxyz0123456789{}_ '
    
    SYMBOL_MAP = {
        '⌘':'a','⌬':'b','⍟':'c','⌖':'d','⎔':'e','⌁':'f','⌂':'g','⌤':'h',
        '⍢':'i','⌇':'j','⍜':'k','⎊':'l','⍥':'m','⌻':'n','⍯':'o','⌼':'p',
        '⍪':'q','⎉':'r','⌰':'s','⍮':'t','⎈':'u','⌥':'v','⌦':'w','⍫':'x',
        '⌨':'y','⍬':'z','⓪':'0','①':'1','②':'2','③':'3','④':'4','⑤':'5',
        '⑥':'6','⑦':'7','⑧':'8','⑨':'9','❴':'{','❵':'}','⁔':'_','░':' ',
    }
    
    # Step 1: percent-decode
    encoded = open('mark.txt').read().strip()
    symbols = urllib.parse.unquote(encoded)
    print(f"[1] After URL decode: {symbols}")
    
    # Step 2: symbol substitution
    alpha   = list(ALPHABET)
    shifted = ''.join(SYMBOL_MAP.get(s, s) for s in symbols)
    print(f"[2] After symbol sub: {shifted}")
    
    # Step 3: reverse positional shift
    result = ''
    pos    = 0
    for ch in shifted:
        if ch in alpha:
            pos   += 1
            idx    = alpha.index(ch)
            result += alpha[(idx - pos) % len(alpha)]
        else:
            result += ch
    
    print(f"[3] After unshift:    {result}")
    print(f"\nFLAG: {result}")


## Flag:

    flagwars{symbolic_madness}
