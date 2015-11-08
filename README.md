# intro_CRAB
Il concetto da capire e' che crab usa un config file (che devi scriverti, chiamiamolo) `ntuple.cfg`.

`ntuple.cfg` chiama `cmsRun cmssw_config.py -opzioni varie`

* Quindi dovrai avere un config file di cmssw da passare a cmsRun e che dovrai testare il locale per essere sicuro
che funzioni.
* Quando cmsRun funziona il locale, devi prepararti in config file di crab per dirgli "va bene, adesso questa cosa che facevo in locale, me la devi fare sulla GRID"

Fase1)
* testare il cmssw_config.py
`cmsRun python/alcaSkimming.py type=MINIAODNTUPLE files=$file maxEvents=1000 isCrab=0 tagFile=config/reRecoTags/phiSym_materialCorrection_ref.py`
* So anche che esiste `cmsDriver` per scrivere il config file di cmssw da dare in pasto a cmsRun

Fase2)
* Scrivere, in qualche modo il config file di crab
* Quando e' pronto il config file di crab: crea i job, li sottometti, ne controlli lo status
```
###SINTASSI DI CRAB2
#source di crab2
crab -cfg tmp/ntuple.cfg -create #crea i job
crab -c prod_ntuples/MINIAODNTUPLE/DoubleEG-ZSkim-Run2015B-PromptReco-v1-miniAOD_test/251022-251883/ -submit 1 #sottomette 1 job; submit 2 ne sottomette 2
crab -c prod_ntuples/MINIAODNTUPLE/DoubleEG-ZSkim-Run2015B-PromptReco-v1-miniAOD_test/251022-251883/ -status
#controlla lo status
crab -c prod_ntuples/MINIAODNTUPLE/DoubleEG-ZSkim-Run2015B-PromptReco-v1-miniAOD_test/251022-251883/ -status -getoutput
```
