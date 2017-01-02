THISDIR := GAelectrodynamics
THISBOOK := GAelectrodynamics
BASEVER := 89da363

include ../latex/make.bookvars

# Override my default:
#MY_CLASSICTHESIS_FRONTBACK_FILES := $(filter-out ../classicthesis_mine/FrontBackmatter/Dedication.tex,$(MY_CLASSICTHESIS_FRONTBACK_FILES))

#ONCEFLAGS := -justonce

SOURCE_DIRS += appendix
FIGURES := ../figures
SOURCE_DIRS += $(FIGURES)

PRIMARY_SOURCES := $(shell grep input chapters.tex | sed 's/%.*//;s/.*{//;s/}.*//;')
PRIMARY_SOURCES += FrontBackmatter/preface.tex

EXTERNAL_DEPENDENCIES += ../ece1229-antenna/MaxwellsStatement.tex
EXTERNAL_DEPENDENCIES += ../ece1229-antenna/MaxwellsTimeHarmonic.tex
EXTERNAL_DEPENDENCIES += ../ece1229-antenna/MaxwellsFieldAndSourceDescription.tex
EXTERNAL_DEPENDENCIES += ../frequencydomain/frequencydomainMaxwellsExtraction.tex
EXTERNAL_DEPENDENCIES += ../frequencydomain/frequencydomainMaxwells.tex
EXTERNAL_DEPENDENCIES += ../frequencydomain/frequencydomainPlaneWaves.tex
EXTERNAL_DEPENDENCIES += ../gabookI/calculus/helmholtzDerviationMultivectorSolution.tex
EXTERNAL_DEPENDENCIES += ../gabookI/calculus/helmholtzDerviationMultivectorStatement.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/stokesAndGreens.tex
EXTERNAL_DEPENDENCIES += ../gabookI/calculus/greensTheorem.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/statement.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/oneparameter.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/twoparameter.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/threeparameter.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/scalarVolumeElement.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/bladeDotWedgeSymmetryIdentitiesTheorem.tex
EXTERNAL_DEPENDENCIES += ../gabookI/appendix/wedgeDistributionIdentity.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/bladeDotWedgeSymmetryIdentities.tex
EXTERNAL_DEPENDENCIES += ../gabookI/appendix/wedgeDistributionIdentityProblems.tex
EXTERNAL_DEPENDENCIES += ../stokesTheorem/stokesTheoremCoreProblems.tex
EXTERNAL_DEPENDENCIES += ../gabookI/calculus/fundamentalTheoremOfCalculus.tex
EXTERNAL_DEPENDENCIES += ../gabookI/calculus/gradientGreensFunction.tex
EXTERNAL_DEPENDENCIES += ../gabookI/calculus/biotSavartGreens.tex
EXTERNAL_DEPENDENCIES += ../gabookI/calculus/helmholtzDerviationMultivector.tex

#GENERATED_SOURCES += matlab.tex 
#GENERATED_SOURCES += mathematica.tex 
#GENERATED_SOURCES += julia.tex 

EPS_FILES := $(wildcard $(FIGURES)/*.eps)
PDFS_FROM_EPS := $(subst eps,pdf,$(EPS_FILES))
#$(error PDFS_FROM_EPS $(PDFS_FROM_EPS))

THISBOOK_DEPS += $(PDFS_FROM_EPS)
#THISBOOK_DEPS += macros_mathematica.sty

CLEAN_TARGETS += *.sp FrontBackmatter/*.sp

include ../latex/make.rules

$(THISBOOK).pdf :: $(EXTERNAL_DEPENDENCIES)

.PHONY: spellcheck
spellcheck: $(patsubst %.tex,%.sp,$(PRIMARY_SOURCES))

%.sp : %.tex
	spellcheck $^
	touch $@

.PHONY: copy
copy : $(HOME)/Dropbox/$(THISDIR)/$(THISBOOK).pdf

$(HOME)/Dropbox/$(THISDIR)/$(THISBOOK).pdf : $(THISBOOK).pdf
	cp $^ $@
