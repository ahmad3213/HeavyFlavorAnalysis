#Taking cmsrel for 2017
cmsrel CMSSW_9_4_2
cd CMSSW_9_4_2/src/
cmsenv
git clone https://github.com/zhenhu/HeavyFlavorAnalysis

scram b
cd HeavyFlavorAnalysis

cd Onia2MuMu/test/2017

voms-proxy-init -voms cms --valid 172:00 <p>
./multicrab_2017_MinBias --crabCmd=submit <p>
./multicrab_2017 --crabCmd=submit <p>
#Following script will loop over all jobs within director (crabOutput2017_)  and will keep resubmitting failing jobs after every 30 mints <p>

nohup python manageCrabTask.py -l -r -t crabOutput2017_ >& crabOutput2017_.log & <p> 

#Taking cmsrel for 2018 <p>
cmsrel CMSSW_10_2_5 <p>
cd CMSSW_10_2_5/src <p>
cmsenv <p>
git clone https://github.com/zhenhu/HeavyFlavorAnalysis <p>
scram b <p>
cd HeavyFlavorAnalysis <p>
cd Onia2MuMu/test/2018 <p>
voms-proxy-init -voms cms --valid 172:00 <p>
./multicrab_2018ABC --crabCmd=submit <p>
./multicrab_2018D --crabCmd=submit <p>
./multicrab_2018ABC_MinBias --crabCmd=submit <p>
./multicrab_2018D_MinBias --crabCmd=submit <p>
#Following script will loop over all jobs within director (crabOutput2018ABC_)  and will keep resubmitting failing jobs after every 30 mints <p>

nohup python manageCrabTask.py -l -r -t crabOutput2018ABC_ >& crabOutput2018ABC_.log & <p>
