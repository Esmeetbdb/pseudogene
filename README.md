# pseudogene
# To run the binomial analysis of pseudogene insert locations do the following steps:

# Step 1: Generate random insert sites
Import MonteCarlo_inserts as MC
MC.MC_generation(10000)

# Step 2: Check chromosomal overrepresentation
Import Binomial_analysis as BinA
BinA.Chromosomal_binomial('Monte_Carlo_Pos_file.txt', 'Unique_insert_file', 'Output_file', chr_index_insert, chr_index_Monte_Carlo)

# Step 3: Tabix track check, repeat for insert file and random insert file
BinA.iterate_track_check('File_paths_to_tabix_files', 'Inserts_file', chr_index, position_index, 'Path_to_output')

# Step 4: Check tabix track overrepresentation
File_location_dict = {'Track name' : ['Unique_inserts_file' , 'Path_to_file_step3_Unique_inserts', 'MC_insert_sites', 'Path_to_file_step3_MC_inserts']}

BinA.iterate_bin_analysis(File_location_dict, 'Output_file.txt')
