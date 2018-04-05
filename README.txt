=======================================================================
PSOVina version 1.1                                                    
Marcus C. K. Ng, Hio Kuan Tai, Hang Lin & Shirley W. I. Siu                                   
                                                                       
Computational Biology and Bioinformatics Lab (CBBio)                        
University of Macau                                                    
                                                                       
Visit http://cbbio.cis.umac.mo for more information.                   
                                                                       
PSOVina was developed based on the framework of AutoDock Vina.                                                                                
For more information about Vina, please visit http://vina.scripps.edu.                                                                       
=======================================================================

0. REQUIRED SOFTWARE
   For successful compilation, please install Boost.  
   from http://www.boost.org. For preparing molecules for docking, 
   please install AutoDockTools (ADT) from http://mgltools.scripps.edu.

1. INSTALLATION

   The installation basically follows the installation of AutoDock Vina. 
   The steps are simple:

     a. unpack the files
     b. cd psovina-1.1/build/<your-platform>/release
     c. modify Makefile to suit your system setting
     d. type "make" to compile
    
    The binary psovina will be generated at the current directory. You can 
    copy this binary to a directory in your PATH e.g. /usr/local/bin, or add
    the path of the current directory to your PATH.

2. RUNNING PSOVINA

   You can run psovina as the way you run vina but additional three 
   parameters (optional) are used to specify how the PSO algorithm performs 
   searching:

   % <path-to-psovina>/psovina

   PSO parameters (optional):
       --num_particles arg (=8)      Number of particles
       --w arg (=0.36)               Inertia weight
       --c1 arg (=0.99)              Cognitive weight 
       --c2 arg (=0.99)              Social weight 

   For example, docking Kifunensine in the Mannosidase enzyme (PDBID 1ps3 from
   the PDBbind v2012 dataset) using PSOVina with default PSO parameters in a 
   8-core computer and return the lowest energy prediction:

   % <path-to-AutoDockTools>/prepare_ligand4.py -l 1ps3_ligand.mol2 \
     -o 1ps3_ligand.pdbqt -A 'hydrogens' -U 'nphs_lps_waters'

   % <path-to-AutoDockTools>/prepare_receptor4.py -r 1ps3_protein.pdb \
     -o 1ps3_protein.pdbqt -A 'hydrogens' -U 'nphs_lps_waters' 

   % <path-to-psovina>/psovina \
     --receptor 1ps3_protein.pdbqt --ligand 1ps3_ligand.pdbqt \
     --center_x  31.951 --center_y 65.5053 --center_z 7.63888 \
     --size_x    33.452 --size_y   27.612  --size_z   35.136  \ 
     --num_modes 1      --cpu 8  
   
   More test cases can be downloaded in our web site. 

3. DEVELOP PSOVINA

   If you are interested in the source code of PSOVina for any academic
   purposes, please note that the following files were newly developed   
   in our work or modified based on Vina:
   	src/main/main.cpp
	src/lib/pso.h
	src/lib/pso.cpp
	src/lib/parallel_pso.h
	src/lib/parallel_pso.cpp
	src/lib/pso_mutate.h
	src/lib/pso_mutate.cpp
	src/lib/pso_search.h
	src/lib/pso_search.cpp

4. CITATION
   Please cite our paper if you have used PSOVina. It would be nice to let us
   know that you found PSOVina useful by sending us an email. 

   (Main)
   Marcus C. K. Ng, Simon Fong, and Shirley W. I. Siu  
   PSOVina: The Hybrid Particle Swarm Optimization Algorithm for Protein-Ligand Docking
   Journal of Bioinformatics and Computational Biology (JBCB), 13 (3), 1541007, 2015. 

   (Further enhancement)
   Hio Kuan Tai, Hang Lin, and Shirley W. I. Siu* 
   Improving the Efficiency of PSOVina for Protein-Ligand Docking by Two-Stage Local Search
   The 2016 IEEE Congress on Evolutionary Computation (CEC2016), To appear in conference proceeding
   Vancouver, Canada, July 24-29, 2016. 

5. CONTACT US
    
   Developer: Marcus C. K. Ng <marcus.ckng@gmail.com>, Hio Kuan Tai <n19931225@yahoo.com.hk>
   Project P.I.: Shirley W. I. Siu <shirleysiu@umac.mo>

   Computational Biology and Bioinformatics Lab, University of Macau
   http://cbbio.cis.umac.mo
   http://www.cis.umac.mo/~shirleysiu

