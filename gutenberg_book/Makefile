BOOKS=alice christmas_carol dracula frankenstein heart_of_darkness life_of_bee moby_dick modest_propsal pride_and_prejudice tale_of_two_cities ulysses

NOMD=$(BOOKS:%=data/%.no_md.txt)
FREQLISTS=$(BOOKS:%=results/%.freq.txt)
SENTEDBOOKS=$(BOOKS:%=results/%.sent.txt)

all: data/all.no_md.txt data/all.freq.txt data/all.sent.txt $(FREQLIST) $(SENTEDBOOKS)
clean:
	rm -f data/*no_md.txt results/*freq.txt results/*sent.txt

%.no_md.txt: %.txt
	python3 src/remove_gutenberg_metadata.py $< $@

results/%.freq.txt: data/%.no_md.txt 
	src/freqlist.sh $< $@

results/%.sent.txt: data/%.no_md.txt
	src/sent_per_line.sh $< $@

data/all.freq.txt: $(FREQLISTS)
	cat $^ > $@

data/all.sent.txt: $(SENTEDBOOKS)
	cat $^ > $@

data/all.no_md.txt: $(NOMD)
	cat $^ > $@
