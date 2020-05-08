all: twofoo.fq.gz gtdb-release89-k31.sbt.zip gtdb-release89-k31.lca.json.gz \


gtdb-release89-k31.sbt.zip:
	curl -L https://osf.io/5mb9k/download > gtdb-release89-k31.sbt.zip

gtdb-release89-k31.lca.json.gz:
    curl -L https://osf.io/gs29b/download > gtdb-release89-k31.lca.json.gz

#
# akker-reads.abundtrim.gz is a collection of reads from podar data
# that maps to the Akkermansia muciniphila ATCC BAA-835 genome via bwa aln.
# "Real" data, with known answer.  There does not appear to be significant
# overlap with other genomes in the Podar data set; so, no significant strain
# variation.
#

akker-reads.abundtrim.gz:
	curl -o akker-reads.abundtrim.gz -L https://osf.io/dk7nb/download

#
# shew-reads.abundtrim.gz is a collection of reads from podar data
# that maps to the Shewanella OS223 genome via bwa aln.  "Real" data,
# with known answer.  Note that there is significant overlap with the
# Shewanella OS185 genome; this is a data set with significant strain
# variation.
#

shew-reads.abundtrim.gz:
	curl -L 'https://osf.io/7az9p/?action=download' > shew-reads.abundtrim.gz

#
# twofoo targets, below, use a synthetic mixture of reads from podar data -
# the shew-reads.abundtrim.gz (mapping to Shewanella baltica OS223) and
# akker-reads.abundtrim.gz (mapping to Akkermansia muciniphila ATCC BAA-835).
# Many of the shew-reads also map to S. baltica OS185, while the akker-reads
# do not; so this is a good mixture for testing the effects of strain variation
# on catlas foo.

# make synthetic mix data set 'twofoo'
twofoo.fq.gz: shew-reads.abundtrim.gz akker-reads.abundtrim.gz
	gunzip -c shew-reads.abundtrim.gz akker-reads.abundtrim.gz | gzip -9c > twofoo.fq.gz
