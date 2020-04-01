# VASP-density-of-state-DOS-
make note to avoid memory losse
The calculate process of DOS, should have threee parts.
The first parts: optimized structures.
Almoust every parts of vasp calculation should start at the optimize process. That is to make the structure more reasonable and near the practic.
INCAR
SYSTM=Ti
ENCUT=400
EDIFF=0.00001
EDIFFG=-0.02
IBRION=2
ISIF=3
NSW=400
ISTART=0
ICHARG=2
ISMEAR=0                  # it is up to your systerm and your choice
SIGMA=0.1                 # it is up to your systerm and your choice
LCHARG=.F.                # save the storage sapce and times
LWAVE=.F.                 # save the storage sapce and times

The second parts: 
static calculate. This process is used to get the charge file (CHGCAR).
mv CONTCAR POSCAR ( use the optimized structure in OUTCAR to be the new POSCAR file)
just change ISIF=2 NSW=0 ICHARG=2 Delet EDIFF EDIFFG. to fix the ions position.
LCHARG=.T. # it is very important to writ down the message of charge density in the CHGCAR file.
remenber the Fermi energy in the vasprun.xml

The third parts:
change ICHARG=10/11
IBRION=-1
NEDOSE=2000 # up to you 
change the Fermi energy ,use the energy get from static calculations.

We should note that, there must contain three parts of calculations. So that the outcome is right.
in the output files vasprun.xml contain the DOS message. you can use p4vasp or vaspkit (11-111 options),to subtract the DOS message.
