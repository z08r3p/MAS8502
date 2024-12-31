java c
MAS8502: Project
Requirements You should submit your project to Canvas no later than 12 noon on Tuesday 14th January.   You   should   submit your report   as   a pdf no   longer than   12   pages,   along   with   a   .Rmd   file   which      contains   the   code   used   to   generate   your   analysis   (i.e.   submit   two   files).
Project brief In   this   project,   you   will   analyse   the   Telemarketing   data   set,   which   describes   the   outcomes   of   telemarketing   attempts   by   a   Portuguese   bank   to   convince   clients   to   take   out   long   term   deposits.You   should   download   the   telemarketing.RData   file   from   Canvas   and   save   it   to   a   suitable   folder   to   contain   your   work.      To   import   the   data   into   R,   set   your   working   directory   to   be   the   folder containing the telemarketing.RData   file, and run the following   line   in   your   R   session:
load("telemarketing.RData")
The   variables   included   in   this   dataset   are:
• age –   The   age   of   the   client;
• marital –   The   client’s   marital   status,   coded   as   1   for   married,   0   otherwise;
• default –   Does   the   client   have   credit   in   default?      Coded   as   1   (yes)      0   (no);
• housing –   Does   the   client   have   a   housing   loan?
• contact – How was the client contacted?    Coded as   1   for   by   mobile   phone,   0   for   landline;
• campaign –   Number   of times   the   client   was   contacted   this   campaign;
• previous –   Number   of times   the   client   was   contacted   before   this   campaign
• emp.var.rate –   Quarterly   employment   variation   indicator
• cons.price.idx –   Monthly   consumer   price   index
• cons.conf.idx –   Monthly   consumer   confidence   index
• euribor3m –   Daily   Euribor   3   month   rate
• y –   Did   the   client   take   out   a   long   term   deposit?    (Target variable)Note   that   the   variables   are      a      mixture   of   demographic    (age,    marital),    financial    (default, housing),          problem-specific          (contact,             campaign,                previous)          and            socio-economic   (emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m) variables.You will   use   a   random   sample   of size   5000   (approximately   12.5%   of the   data)   for your   project,   where   your   specific   data   will   be   based   on   your   student   number.   To   extract   your   specific   data,   run   the   following   code:set.seed(my_student_number) # REPLACE my_student_number with your student number
take_rows <- sample(1:nrow(telemarketing), 5000, replace = F)
my_data <- telemarketing[take_rows, ]
The   resulting   data   frame   called   my_data   should   be   used   for   your   analysis.
Task Your      goal    is      to      build    a      classifier    for    y   –      whether    or    not      the    client      took    out    a    long      term   deposit    (i.e.    whether      the      telemarketing      was      successful      for      that      individual),    using    (at    least   some   of)   the      11   available   predictors.         It   should   be   stressed   that   this   is   a   real   data   set   and   there   is   no   “correct”   answer.   Instead,   what   is   required   is   evidence   of an   understanding   of the   main   statistical   ideas,   sound   interpretation   of   results,   sensible   and   reasoned   comparisons   of   classifiers,   and   demonstration   of competence   in   the   use   of   R   as   a   tool   for   data   analysis.
Things to Consider 
•    Consider    carefully    how    you    will    clean    and    process    the    data,    e.g.       through    handling   housing   = 'unknown',    or   the   response      (target)   variable,   y,   being   classified   as   of   type character;
•    Make   sure   to   include   some   exploratory   data   analysis,   how   can   you   represent   these   vari-   ables   (and the   relationships   between them)   numerically   and   graphically?    What   can   you      say   about   these   relationships   prior   to   model   fitting?
•   You should consider a variety of different modelling approaches with different approaches   to   variable   selection –   where   possible   you   should   make   sure   to   explain   the   model   design   decisions      you      have      made.       Again    this    is    a    real    dataset,    and    so    there      will      be      several   perfectly valid approaches here, just be sure   to   explain   what   you   have   done   and   why   you   have   done   it.    You   ought   to   consider   at   least   one   method   of   regularised   regression代 写MAS8502: ProjectSQL
代做程序编程语言   and   compare   and   contrast   regression   method(s)   with   those   from   discriminant   analysis.
•    Make sure to include a discussion   of inferences   from   your   models   as   well   as   how   well   they   predict – which variables were/weren’t   useful   predictors   of whether   the   campaign   would   be   successful?   What   was   the   effect   of the   variables   which   were   significant?
•    Consider   how   you   can   report   and   compare   the   effectiveness   of   your   different   classifiers   in   a   way   that   is   fair.   Which   model   performs   best?   What   are   your   conclusions?
Writing the report •   You   should   experiment with   different plots   and   commands   using the   console   directly   (or
in   a   .R   file   that   you   use   for   exploration).
•      However,      when   you’re   creating   the   report,      you   must   put   the   text   that   describes   you   findings and the R   code required to produce the   plots   or   numbers   in   a   single   R   Markdown   file   (with   extension      .Rmd)
•      The            main            exceptions            are            the            commands            setwd(), View()   and            (potentially)   install.packages().             Never      include      these         commands      in      an      R      Markdown      file      as these   are   details   that   are   specific   to   each   person’s   computer.
•      Do   not   pre-generate   the   results,   save   the   plots,   and   then   manually   put   the   plots   into   a   Word   document   (or   equivalent)   that   contains   the   text.    The   plots   and   numbers   should   be   generated   automatically   when   you   click   the   Knit   button   in   RStudio.      This   is   a   much   more   eﬀicient   approach.
•    Related   to   the   above,   do   not   generate   a   Word   or   HTML   document   using   the   .Rmd   file   and   then   print   it   as   a   PDF.   Again,   this   is   the   wrong   approach   because   it   is   less   eﬀicient   and   because   the   formatting   of HTML   and   PDF   files   is   deliberately   quite   different   (you   wouldn’t   expect   a   web   page   to   look   the   same   as   a   printed   report).
•    One   option   that   is   useful   if   you   want   to   hide   code      (e.g.,   due   to   a   page   limit)   is   to   set   echo = FALSE in    knitr::opts_chunk$set(echo = FALSE).    For    this    assessment,    you   don’t   need   to   show   your   R   code   in   the   PDF   because   you   have   to   submit   the   Rmd   file   as   well,   where   I   will   be   able   to   see   your   code.
Marking criteria 
Reports   will   be   marked   on   the   university   scale.      Credit   will   be   given   for:
•    Mathematical   accuracy –   How   well   you   apply   the   statistical   techniques   in   your   report.
•    Methodology –   An   understanding   of why   you   have   chosen   the   techniques   that   you   have,   and   what   their   output   means   in   terms   of your   investigation.
•    Critical evaluation – A discussion   of the   strengths   and   weaknesses   of your   methods,   how   things   could   be   improved,   etc.
•      Report structure and presentation – How well your report is written in terms of structure,
how well it flows, and so on   (i.e., aiming for   a   single,   coherent   piece   of writing, as   opposed to   lots   of separate   answers jammed   together)
•    Reproducibility   –   Can   I   reproduce   your   report   using   the   .Rmd   file?      You   can   check   the   repro- ducibility by copying your   files   to   another   computer,   and   see   if RStudio   generates   the   same   report   without   errors.
•      Extra      credit      will      be      given      for      any      reading/techniques      implemented      from      outside      the   scope   of   the   module,   but   this   is   not   a   requirement   to   receive   a   good   mark.      Similarly,   any   investigations   carried   out   beyond what was   described   in the   report task   will   also   be   considered   for   extra   credit.
As   such,   the   marking   scale   (out   of   100)   will   be:
•    80+   (Upper   distinction) –   A   publication   quality   piece   of work.
•    70   −   79   (Lower   Distinction) –   A   very   good   piece   of work   showing   strong   understanding.
•      60   −   69   (Merit) –   A   solid   attempt,   mostly   hitting   the   main   points.
•    50   −   59   (Pass) –   More   good   than   bad,   but   clear   areas   to   improve.
•   < 50 (Fail) – Significant things went wrong or weren’t attempted.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
