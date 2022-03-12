---
title: The ADHD Hacker
published: true
---

The creator of this challenge is John Hammond and if you have seen any of his videos or completed other challenges from him you know it’s going to fun.

> clue: Caesar caesar, on the wall, who is the fairest of them all?

Taking a look at our file we can guess, correctly, that this is a caesar shift cipher.

```

     Bu obl! Jbj, guvf jnezhc punyyratr fher   bf V !erugrtbg ghc bg ahs sb gby n fnj 
    qrsvavgryl nofbyhgryl nyjnlf ybir gelvat   ftavug rivgnibaav qan jra ch xavug bg 
       gb qb jvgu gur irel onfvp, pbzzba naq   sb genc gfevs ruG !frhdvauprg SGP pvffnyp 
     lbhe synt vf synt{whyvhf_ naq gung vf n   tavuglerir gba fv gv gho gengf gnret 
 gung lbh jvyy arrq gb fbyir guvf punyyratr.    qan rqvu bg tavleg rxvy g'abq V 
  frcnengr rnpu cneg bs gur synt. Gur frpbaq   bq hbl gho _n_av_ fv tnys rug sb genc 
   arrq whfg n yvggyr ovg zber. Jung rknpgyl   rxnz qan leg bg reru rqhypav rj qyhbuf 
     guvf svyyre grkg ybbx zber ratntvat naq   ?fravyjra qqn rj qyhbuF ?ryvujugebj 
    Fubhyq jr nqq fcnprf naq gel naq znxr vg   uthbar fv fravy lanz jbU ?ynpvegrzzlf 
 gb znxr guvf svyyre grkg ybbx oryvrinoyr? N    n avugvj ferggry sb renhdf qvybf 
 fvzcyr, zbabfcnpr-sbag grkg svyr ybbxf tbbq   rug gn gfbzyn rj reN .rz bg uthbar 
   raq? Vg ybbxf yvxr vg! V ubcr vg vf tbbq.   }abvgprysre fv tnys ehbl sb genc qevug ruG 
naq ng guvf cbvag lbh fubhyq unir rirelguvat   ebs tnys fvug gvzohf bg qrra hbl gnug 
    cbvagf. Gur ortvaavat vf znexrq jvgu gur   ,rpneo lyehp tavarcb rug qan kvsrec tnys 
  naq vg vapyhqrf Ratyvfu jbeqf frcnengrq ol   lyehp tavfbyp n av qar bg ,frebpferqah 
  oenpr. Jbj! Abj GUNG vf n PGS! Jub xarj jr   fvug bg erucvp enfrnp rug xyvz qyhbp 
            rkgrag?? Fbzrbar trg gung Whyvhf   !ynqrz n lht enfrnP 
```
Let’s try to decode it. Instead of writing my own code to brute force the shift key and then decode the text I am going to use `dcode.fr`.

```
OHBOYWOWTHISWARMUPCHALLENGESUREOSIREHTEGOTTUPOTNUFFOTOLASAWDEFINITELYABSOLUTELYALWAYSLOVETRYINGSGNIHTEVITAVONNIDNAWENPUKNIHTOTTODOWITHTHEVERYBASICCOMMONANDFOTRAPTSRIFEHTSEUQINHCETFTCCISSALCYOURFLAGISFLAGJULIUSANDTHATISAGNIHTYREVETONSITITUBTRATSTAERGTHATYOUWILLNEEDTOSOLVETHISCHALLENGEDNAEDIHOTGNIYRTEKILTNODISEPARATEEACHPARTOFTHEFLAGTHESECONDODUOYTUBANISIGALFEHTFOTRAPNEEDJUSTALITTLEBITMOREWHATEXACTLYEKAMDNAYRTOTEREHEDULCNIEWDLUOHSTHISFILLERTEXTLOOKMOREENGAGINGANDSENILWENDDAEWDLUOHSELIHWHTROWSHOULDWEADDSPACESANDTRYANDMAKEITHGUONESISENILYNAMWOHLACIRTEMMYSTOMAKETHISFILLERTEXTLOOKBELIEVABLEAANIHTIWSRETTELFOERAUQSDILOSSIMPLEMONOSPACEFONTTEXTFILELOOKSGOODEHTTATSOMLAEWERAEMOTHGUONEENDITLOOKSLIKEITIHOPEITISGOODNOITCELFERSIGALFRUOYFOTRAPDRIHTEHTANDATTHISPOINTYOUSHOULDHAVEEVERYTHINGROFGALFSIHTTIMBUSOTDEENUOYTAHTPOINTSTHEBEGINNINGISMARKEDWITHTHEECARBYLRUCGNINEPOEHTDNAXIFERPGALFANDITINCLUDESENGLISHWORDSSEPARATEDBYYLRUCGNISOLCANIDNEOTSEROCSREDNUBRACEWOWNOWTHATISACTFWHOKNEWWESIHTOTREHPICRASEACEHTKLIMD
```

We got some clear words with a 13 shift key. Something is off though. The clue suggests to us that it is mirrored but we did get some english words from the 13 shift. Let’s try to clean this up and see what se can figure out.

```
OH BOY! WOW, THIS WARMUP CHALLENGE SURE    OSIREHTEGOTTUPOTNUFFOTOLASAW
DEFINITELY ABSOLUTELY ALWAYS LOVE TRYING   SGNIHTEVITAVONNIDNAWENPUKNIHTOTTODOWITH
THE VERY BASIC COMMONAND                   FOTRAPTSRIFEHTSEUQINHCETFTCCISSALC
YOUR FLAG IS FLAG{JULIUS_ AND THAT IS      AGNIHTYREVETONSITITUBTRATSTAERG
THAT YOU WILL NEED TO SOLVE THIS CHALLENGE DNAEDIHOTGNIYRTEKILTNODISEPARATEEACH
PART OF THE FLAG THESE                     CONDODUOYTUBANISIGALFEHTFO
TRAP NEED JUST A LITTLE BIT MORE WHAT EXACTLY    EKAMDNAYRTOTEREHEDULCNIEWDLUOHSTHIS
FILLER TEXT LOOK MORE ENGAGING AND         SENILWENDDAEWDLUOHSELIHWHTROW
SHOULD WE ADD SPACES AND TRY AND MAKE IT   HGUONESISENILYNAMWOHLACIRTEMMYS
TO MAKE THIS FILLER TEXT LOOK BELIEVABLE   AANIHTIWSRETTELFOERAUQSDILOS
SIMPLE MONOSPACE FONT TEXT FILE LOOKS GOOD EHTTATSOMLAEWERAEMOTHGUONEEND
IT LOOKS LIKE IT I HOPE IT IS GOOD         NOITCELFERSIGALFRUOYFOTRAPDRIHTEHT
AND AT THIS POINT YOU SHOULD HAVE EVERY THING   ROFGALFSIHTTIMBUSOTDEENUOYTAHT
POINTS THE BEGINNING IS MARKED WITH THE    ECARBYLRUCGNINEPOEHTDNAXIFERPGALF
AND IT INCLUDES ENGLISH WORDS SEPARATED BY YLRUCGNISOLCANIDNEOTSEROCSREDNUBRACEWOWNOW
THAT IS ACTF WHO KNEW                      WESIHTOTREHPICRASEACEHTKLIMD
```

It seems that only part of it is decrypted with the 13 shift key but we did get the first part of the flag `flag{julius_`. Looking at the clue we know that part of it is likely mirrored. Lets that the original right half of the text file and reverse it.

`rev caesarmirror.txt`

You will get an output right to the terminal but we should probably get that in a file cm-rev-message2.txt

`rev caesarmirror.txt >> cm-rev-message2.txt`

Ok, I cleaned up the spaces a bit and used the multi-cursor feature of Sublime Text to select just the decrypted text and then it’s back to dcode.fr

```
was a lot of fun to put together! I so    
to think up new and innovative things    
classic CTF techniques! The first part of
great start but it is not everything      
I don't like trying to hide and          
part of the flag is _in_a_ but you do    
should we include here to try and make    
worthwhile? Should we add newlines?      
symmetrical? How many lines is enough    
solid square of letters within a          
enough to me. Are we almost at the        
The third part of your flag is reflection}
that you need to submit this flag for    
flag prefix and the opening curly brace,  
underscores, to end in a closing curly    
could milk the caesar cipher to this      
Caesar guy a medal!
```

Great, let’s put it all together to get our flag.

```
 Oh boy! Wow, this warmup challenge sure was a lot of fun to put together! I so
   definitely absolutely always love trying to think up new and innovative things  
      to do with the very basic, common and classic CTF techniques! The first part of
    your flag is flag{julius_ and that is a great start but it is not everything
that you will need to solve this challenge. I don't like trying to hide and
 separate each part of the flag. The second part of the flag is _in_a_ but you do
  need just a little bit more. What exactly should we include here to try and make
    this filler text look more engaging and worthwhile? Should we add newlines?
   Should we add spaces and try and make it symmetrical? How many lines is enough
to make this filler text look believable? A solid square of letters within a
simple, monospace-font text file looks good enough to me. Are we almost at the
  end? It looks like it! I hope it is good. The third part of your flag is reflection}
and at this point you should have everything that you need to submit this flag for
   points. The beginning is marked with the flag prefix and the opening curly brace,  
 and it includes English words separated by underscores, to end in a closing curly
 brace. Wow! Now THAT is a CTF! Who knew we could milk the caesar cipher to this
           extent?? Someone get that Julius Caesar guy a medal!
```

Our flag for this challenge is: `flag{julius_in_a_reflection}`

I had a lot of fun with this challenge and if you're new to cryptography it can teach you to look at encryption as more that something that needs to be cracked or decoded. Sometimes you have to deal with nested encryption, salted encryption, and more. 