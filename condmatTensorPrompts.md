#Common Prompts
1. Read plans/ to confirm the develop rules and style. And understand current developing phase.
0. update plans,developLog,etc.(this is standard process of developing and should be a rule of develop)

#interface 260124
## baseTensor✅
Here is the plan of extending API of core.base.BaseTensor:
1. Read plans/ to confirm the develop rules and style. And understand current developing phase.
2. As future manybody development needs to distinguish category of orbitals, the orbitals_names should have a more powerful form:
2.1. current str of one orbital can be "Ce1(or atom1)-dxy-spin_up-local-U7.0" to represent site-orbital-spin(may have no spin)-local or conductive (some times switch off)- value of Hubbard U.
2.2. then add a orbital_metadatas (if have this one, ignore orbital_names) as a List of dictionary(site:Ce1;orb:dxy;etc.)
3. update plans,developLog,etc.(this is standard process of developing and should be a rule of develop)

##nameChange✅
Here is a further plan of changing name of parameters Lattice.model.TightBindingModel to Lattice.model.HoppingModel:
1. Read plans/ to confirm the develop rules and style. And understand current developing phase.
2. The name of TightBindingModel is misleading, because neither H(k) or H(R) in it force nearest neighbor hopping. So change the name to HoppingModel and fix all modules and examples use it!
3. update plans,developLog,etc.(this is standard process of developing and should be a rule of develop)

##plot adding✅
Here is a plan to upgrade analysis.dos and analysis.bandstr:
1. Read plans/ to confirm the develop rules and style. And understand current developing phase.
2. Read all kagome examples, they output png like band,dos,band+dos,band coloared by weight of certain orbitals. the effect of setting are great, so put several plot style as default setting plotting methods of those two sub modules, so user can use one line to draw the output of one H(R) or H(k)
3. Change examples one by one to use the one-line plotting commend
0. update plans,developLog,etc.(this is standard process of developing and should be a rule of develop)

##interface
###interface:hr->Hopping
Here is the plan of interface coding:
1. Read plans/ to confirm the develop rules and style. And understand current developing phase.
2. The aim is to read a hr.dat and orbital_metadatas(a parameter of BaseTensor,model.HoppingModel), then store it into a Lattice.model.HoppingModel.build_HR. In future, we will add a translation from wannier90/wanniertools 's site+orbital+spinor format to orbital_metadatas. i.e. wt.in -> metadatas, so prepare for future implement
3. Because in the method "build_HR" there is no limitation whether R being continuum or discrete, so it is a natrual choice to store hr
4. generate kagome_hr.dat to verify the result: refer to examples/kagome_f_effective_array.py for the hopping.
PS: The so-called "hopping terms" in the wannier_hr.dat file are actually the matrix elements of the Hamiltonian in the Wannier function basis for various wannier orbitals. One has to identify the matrix elements corresponding to the on-site, nearest, next nearest neighbour atoms and so on...for the different orbitals.This can be used in constructing the hopping Hamiltonian matrix as hopping term between various orbitals, then finding the eigenvalues of the TB matrix which are the dispersion relations. And it is similar from hr.dat to hopping model:Lattice.model.HoppingModel.
5. update plans,developLog,etc.(this is standard process of developing and should be a rule of develop)

###hr->Hopping examples
Here is the plan of an large-data example of interface:
1. Read plans/ to confirm the develop rules and style. And understand current developing phase.
2. From https://github.com/quanshengwu/wannier_tools/tree/master/examples/Co2MnGa download wannier90_hr.dat.tar.gz and wt.in in data/ as examples.
3. Add a translation from wannier90/wanniertools 's site+orbital+spinor format to orbital_metadatas. i.e. wt.in -> metadatas
4. translate them into a hoppingModel and run similar analysis like kagome examples(bandstr,dos,effective JSmodel while Co-d is local)
