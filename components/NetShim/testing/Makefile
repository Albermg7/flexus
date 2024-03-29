# DO-NOT-REMOVE begin-copyright-block 
#
# Redistributions of any form whatsoever must retain and/or include the
# following acknowledgment, notices and disclaimer:
#
# This product includes software developed by Carnegie Mellon University.
#
# Copyright 2012 by Mohammad Alisafaee, Eric Chung, Michael Ferdman, Brian 
# Gold, Jangwoo Kim, Pejman Lotfi-Kamran, Onur Kocberber, Djordje Jevdjic, 
# Jared Smolens, Stephen Somogyi, Evangelos Vlachos, Stavros Volos, Jason 
# Zebchuk, Babak Falsafi, Nikos Hardavellas and Tom Wenisch for the SimFlex 
# Project, Computer Architecture Lab at Carnegie Mellon, Carnegie Mellon University.
#
# For more information, see the SimFlex project website at:
#   http://www.ece.cmu.edu/~simflex
#
# You may not use the name "Carnegie Mellon University" or derivations
# thereof to endorse or promote products derived from this software.
#
# If you modify the software you must place a notice on or within any
# modified version provided or made available to any third party stating
# that you have modified the software.  The notice shall include at least
# your name, address, phone number, email address and the date and purpose
# of the modification.
#
# THE SOFTWARE IS PROVIDED "AS-IS" WITHOUT ANY WARRANTY OF ANY KIND, EITHER
# EXPRESS, IMPLIED OR STATUTORY, INCLUDING BUT NOT LIMITED TO ANY WARRANTY
# THAT THE SOFTWARE WILL CONFORM TO SPECIFICATIONS OR BE ERROR-FREE AND ANY
# IMPLIED WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE,
# TITLE, OR NON-INFRINGEMENT.  IN NO EVENT SHALL CARNEGIE MELLON UNIVERSITY
# BE LIABLE FOR ANY DAMAGES, INCLUDING BUT NOT LIMITED TO DIRECT, INDIRECT,
# SPECIAL OR CONSEQUENTIAL DAMAGES, ARISING OUT OF, RESULTING FROM, OR IN
# ANY WAY CONNECTED WITH THIS SOFTWARE (WHETHER OR NOT BASED UPON WARRANTY,
# CONTRACT, TORT OR OTHERWISE).
#
# DO-NOT-REMOVE end-copyright-block   

#COPTS=-I.. -Wall -g -O0 -DNS_STANDALONE #-pg -a 
COPTS=-I.. -Wall -g -O0 -DNS_STANDALONE -DLOG_RESULTS

PROGS=netshim torus 
PROGS+=kn truss # CMU-ONLY

all: $(PROGS)

OBJS = \
	../netcontainer.o \
	../netnode.o \
	../netcommon.o \
	../channel.o \
	../netswitch.o \
	regress.o \
	histogram.o

.cpp.o:
	$(CXX) -c $(COPTS) $(INCLUDE) -o $@ $<

.c.o:
	$(CXX) -c $(COPTS) $(INCLUDE) -o $@ $<

clean:
	rm -f *~ *.o $(TARGET) core $(OBJS) $(PROGS)

netshim: $(OBJS) main.o
	$(CXX) -o $@ $(COPTS) $+ $(LIBS)

torus:	torus.o
	$(CXX) -o $@ $(COPTS) $< $(LIBS)

topology:	topology.o
	$(CXX) -static -o $@ $(COPTS) $< $(LIBS)

# CMU-ONLY-BLOCK-BEGIN
kn:	kn.o
	$(CXX) -o $@ $(COPTS) $< $(LIBS)

truss:	truss.o $(OBJS)
	$(CXX) -o $@ $(COPTS) $+ $(LIBS)
# CMU-ONLY-BLOCK-END
