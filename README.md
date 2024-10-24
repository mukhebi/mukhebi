#! /bin/bash
For reads in `cat /home/user/&lt;file path&gt;/fastq.txt`
do
TrimmomaticPE-phred33
/home/user/cashew/cashew_project/&lt;file.path&gt;/${reads}1.fastq.gz/home/user/cashew/cashew
_project/&lt;file.path&gt;${reads}2.fastq.gz ./${reads}1.trim.fastq ./${reads}1.untrim.fastq
./${reads}2.trim.fastq ./${reads}2.untrim.fastq ILLUMINACLIP: NexteraPE-PE.fa:2:30:10
LEADING: 3 TRAILING: 3 SLIDINGWINDOW: 4:15 MINLEN: 36.
Done
#! /bin/bash
For reads in `cat /home/user/&lt;file. Path&gt;/fastq.txt`
do
Vsearch -fastq_mergepairs /home/user/&lt;file. Path&gt;/${reads}_1.trim.fastq -reverse
/home/user/&lt;file. Path&gt;/${reads}_2.trim.fastq -fastq_maxdiffs 10 -fastq_minovlen 10 -
fastq_truncqual 2 -fastq_allowmergestagger -fastq_minlen 1 -fastq_minmergelen 1 -fastaout

187

/home/user/&lt;file.path&gt;/${reads}.merged.fasta–eetabbedout/home/
user/&lt;file.path&gt;/${reads}.tb
done

#! /bin/bash
For reads in `cat /home/user/&lt;file. Path&gt;/fastq.txt`
Do
sed -e &quot;s/\(^@.*\) .*$/\1;sample=${reads%.*};/&quot; ../&lt;file. Path&gt;/$reads &gt;&gt; &lt;file.name&gt;;
Done
APPENDIX V : Sequence processing: The command line codes used for both ITS and
D1/D2 28S rRNA. Of the epiphytic and endophytic quality sequence reads.
Read Filtering: (vsearch --fastx_filter &lt;input.fastq/fasta&gt; --fastq_maxee 1 –fastaout
&lt;output.fasta)
Removal of dulicate reads: (vsearch –derep_fulllength &lt;input.fasta&gt; --output &lt;output.fasta
–sizeout –relabel ASV)
Read Denoising:  (vsearch –cluster_unoise &lt;input.fasta&gt; --minsize 4 –unoise_alpha 2
–centroids &lt;output.fasta&gt;)
Denovo chimera removal: (vsearch –uchime3_denovo &lt;input.fasta –nonchimeras
&lt;output.fasta&gt;)
ASV Clustering into OUT: (vsearch –cluster_size &lt;input.fasta&gt; --id 0.97 –centroids
&lt;otu.fasta&gt; --sizein –relabel out)
Mapping of OUTs to Raw reads (creation of OTU Table count): (vsearch –usearch_global
&lt;reads.fasta&gt; -db out.fasta –id 0.97 –otutabout &lt;output.tsv)

188

OTU Alignment: (mafft –thread 4 –globalpair –maxiterate 1000 &lt;input.fasta&gt; 
&lt;output.fasta&gt;)
Tree building:  (Fastree –gtr –nt &lt;input.fasta&gt; &lt;output.tre&gt;)
Local BLAST database:  (makeblastdb –in &lt;input.fasta&gt; -out &lt;database name&gt; -dbtype
&lt;nucl&gt; -title &lt;”fungal database” &gt; -seqids)
Creating taxa file:  (blastn –query &lt;out.fasta&gt; -db ref_seq.fasta –evalue 10e-21, -outfmt ‘6
std’ &lt;–output. Taxa&gt;
Taxa file cleaning: (removal of underscores): sed –I ”s/;/\t/g&quot; &lt;filename&gt;  and sed -i
&#39;s/\(\w\+\)__//g&#39; &lt;filename&g
