
# Exit code methods:
# -D EXIT_SHISH=1      -- run invalid opcode 0xFC for passing tests, and
#                         0xFD for failing ones
# -D EXIT_MOONEYE=1    -- run opcode 0x40 (LD B,B) to exit, set regs
#                         B/C/D/E/H/L = 3/5/8/13/21/34 for success or
#                         anything else for failure
# neither of the above -- original blargg exit signal: print "Passed" or
#                         "Failed" on the link port

all: $(shell ls -1 *.s | sed s/.s$$/.gb/g)

clean:
	rm -f *.o *.link *.gb

%.gb: %.link %.o Makefile
	wlalink $< $@

%.link: %.o Makefile
	printf "[objects]\n$<\n" > $@

%.o: %.s common/* Makefile
	wla-gb -D EXIT_SHISH=1 -D "TEST_NAME=\"$$(echo $< | sed 's/_/ /; s/\.s//')\"" -o $@ $<
