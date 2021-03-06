---
title: ZnunuB colorflow
date: '2017-07-19'
tags:
- colorflow
- znunub
- zvvb
---
[Original note : Samples comparison 1](quiver-note-url/634983E1-784F-4416-9F59-5F235DA0BE8E)
)
Purpose : understand why loose selection shows similar pull angle distributions in ZvvB and ZHvvbb, while tight selection does not
Context : different shapes looking at the pull angle distribution of the leading jet before (2bjets required) and after all VHbb cuts
Conclusion : ZvvB pull angle distribution is flattened by the mBB [100, 150] GeV cut (?)
)
## Loose selection
![dTheta1L_4.png](/images/q/32954D0D1E44033D384C5FA3370898A7.png)
Procedure : draw the pull angle distribution at each step of the cutflow
)
# Selection
| step | bool              | pass                                           |
| ---- | ----------------- | ---------------------------------------------- |
| 0    | all               | at least 2 jets reconstructed                  |
| 1    | pass2BJets        | exactly 2 b-jets (B-hadrons ConeExclHadF)      |
| 2    | passJetAccept     | pT > 20 GeV, abseta < 2.5                      |
| 3    | passMBB           | mBB in [100, 150] GeV                          |
| 4    | passMET           | MET > 130 GeV to enhance stat. (158 GeV at ME) |
| 5    | passdPhiBB        | dPhiBB < 140                                   |
| 6    | passdPhiVBB       | dPhiVBB > 120                                  |
| 7    | passmindPhiMETJet | mindPhiMETJet > 20                             |
)
# Plots
## all
![dTheta1_4_cut0.png](/images/q/302CD38D21BFC769C006710D72E0A326.png)
