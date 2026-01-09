---
layout: post
title: Developer Diary, International Day of Democracy
date: 2025-09-15 08:02:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, codeberg-move, mini-server]
summary: Progress on assorted projects
thumbnail: /blog/assets/discurso-funebre-pericles.png
offset: -30%
description: This week's projects include my mini-server, the blog's code, my JSON Resume theme, Socialite tools, the Silver Bat text, Mystic T-Square, Chasing Phantoms, Picture-to-Nonogram, and the CPREP background generator, mostly moving to Codeberg.
spell: nonogram cprep Cryptpad Forgejo Inf Jellyfin Radicale YaCy Ollama Philipp Foltz eval bloviation Vec jsonresume sfx ChasingPhantoms nonograms
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the [International Day of Democracy](https://en.wikipedia.org/wiki/International_Day_of_Democracy), a day to assert that we have "no single model of democracy and that democracy does not belong to any country or region," in defiance of people who want to tell you that *those people* should probably stick to one-party rule and military dictatorships, or who want to tell you that democracy has failed, and we should make our way back to aristocratic Apartheid states.

By the way, random observation, have you ever noticed the almost complete overlap between people who will try to insist that the United States doesn't qualify as a democracy[^1] and the people who believe that the phrase "toxic masculinity"[^2] asserts that men have some inherent toxicity?

[^1]:  They argue that we don't bring the entire population to Washington every time we need to make a decision.  They would never say anything bad about the white supremacy, the misogyny, the unregulated capitalism, or the voter suppression that make us less democratic.  In my experience, they *really* don't like it when you point out that "democratic republic" has most of the word "democracy" in it for a deliberate reason...

[^2]:  The narrow variety of masculinity that obsesses over hierarchies designed around physical strength and virility.

![Pericles Gives the Funeral Speech, in which he praised democracy, among other Athenian values](/blog/assets/discurso-funebre-pericles.png "The dog (left-most on the inexplicable right-hand platform) would later grow disillusioned and start the Dog Liberation Movement.  If somebody has an era-appropriate pun for that, feel free to amend the post...")

With that, on to the week's projects.

## Mini-Server, Part 10

I had a bit of a shock, this week, when I discovered something had replaced the landing pages that I created for my Raspberry Pi-turned-servers with the default NGINX landing page.  It looks like NGINX considers itself to have ownership over those pages, meaning that it might overwrite you during an update.

Oh, well.  I saved a copy as a draft, so it didn't waste too much effort to pick out the dozen links to [2FAuth](https://2fauth.app/), [Code Server](https://github.com/coder/code-server), [Cryptpad](https://cryptpad.org/), [Fresh RSS](https://freshrss.org/), [Forgejo](https://forgejo.org/), [Inf Cloud](https://inf-it.com/open-source/clients/infcloud/), [Jellyfin](https://jellyfin.org/), [Own Tracks](https://owntracks.org/), [Parchment](https://github.com/curiousdannii/parchment), [Radicale](https://radicale.org/v3.html), [Snappy Mail](https://snappymail.eu/), and [YaCy](https://yacy.net/).  [Ollama](https://ollama.com/) doesn't get a link on the pages, since I don't use it as a chatbot.

Speaking of the last item, I discovered another viable use for Ollama, so-called [embedding models](https://ollama.com/blog/embedding-models).  These LLMs (thank goodness) don't bother to try communicating.  Rather, they turn the input text, such as a paragraph, into a multidimensional semantic value.  The chatbots use these to estimate your intent, for example, and that guides how they respond.  For example, the first paragraph in this section ("I had a bit of a shock...") gives me the following monster, courtesy of Snowflake's Arctic Embed 2.0 model.

```JSON
{
  "model": "snowflake-arctic-embed2",
  "embeddings": [
    [
      -0.060585517, 0.047636688, -0.015491335, 0.018616376,
      0.01719394, -0.042980146, 0.06404873, 0.03915874,
      -0.017170275, 0.0041146367, 0.027293604, -0.031446554,
      0.020335447, -0.010262448, -0.041943695, 0.018908696,
      0.09686769, 0.0100457985, -0.054067716, 0.0765989,
      -0.12032362, -0.003305648, 0.033786114, 0.020038212,
      0.020993548, 0.00799743, 0.034408435, -0.0068214834,
      0.033007257, -0.038564894, -0.018488593, -0.06082924,
      0.019719498, -0.025303314, -0.048755325, -0.12828183,
      -0.021906976, 0.025313422, 0.008972054, -0.0116959615,
      -0.0070144157, 0.05765513, -0.0004058156, -0.046598557,
      0.06999514, -0.033665374, 0.05642511, 0.018441485,
      -0.0030695288, -0.022528049, 0.011756799, 0.03423484,
      0.012792017, -0.0880856, -0.04783866, 0.07953132,
      -0.013981234, 0.034216687, 0.08196257, 0.022689354,
      -0.102543056, -0.0470772, -0.02279949, -0.06409554,
      -0.039067578, 0.013985117, 0.0007411008, -0.008469837,
      -0.051804043, -0.013849965, 0.044019464, 0.0033305166,
      0.028283702, 0.027545864, 0.006118028, 0.013095707,
      -0.021510376, -0.05988303, 0.072831035, -0.023326144,
      0.06541805, 0.033821486, 0.012918605, 0.03710524,
      0.0062256125, -0.0005159004, -0.0474326, -0.021494197,
      -0.012940489, -0.06136008, 0.0035629112, -0.035386663,
      0.048947223, -0.031286288, -0.053532265, 0.04651802,
      0.015308419, -0.0268091, 0.036550112, 0.0034281716,
      0.04220949, -0.046049215, 0.03197018, -0.069724806,
      -0.01819673, 0.035599835, 0.011388352, -0.009706316,
      -0.09036306, -0.032481246, -0.012444954, 0.009333144,
      0.02354544, -0.0055969097, 0.011769154, -0.03961452,
      -0.013076609, -0.08761205, -0.03288246, 0.073441066,
      -0.012301795, -0.035660718, 0.008346724, 0.03939218,
      0.024855034, -0.036953762, 0.019560471, 0.012046009,
      0.03036436, 0.0054534418, -0.012823886, -0.02100041,
      0.017959205, -0.008963074, -0.04921588, 0.054051217,
      -0.016397493, 0.0023033707, -0.0035912683, -0.020928724,
      -0.0472345, 0.12524855, -0.05961096, -0.014592261,
      0.040439025, -0.0035314509, 0.0061844145, 0.012189439,
      -0.048848145, -0.043102976, 0.013500538, -0.05053004,
      -0.006709684, 0.029188938, -0.025536383, -0.015495193,
      -0.008202416, 0.009763323, 0.014686185, 0.028942186,
      -0.08748399, -0.0032238052, -0.04177418, 0.016734635,
      -0.014220072, 0.0051299436, 0.02146787, -0.04502006,
      -0.03504636, 0.00021871759, -0.025242368, -0.010538952,
      0.041751035, -0.0130779715, 0.045055285, 0.023110548,
      0.021058602, -0.016992804, 0.023507256, 0.0054457374,
      -0.00026238768, -0.016018298, 0.041950736, 0.047759302,
      -0.030117946, -0.033382464, 0.0047253454, -0.002908008,
      -0.057443015, -0.08382975, 0.039812356, -0.014842902,
      0.06920262, 0.001647172, 0.0257046, 0.06572241,
      -0.0371197, 0.021852553, 0.07388413, 0.039250877,
      -0.00036044317, 0.023022644, 0.08061463, 0.01683956,
      -0.04289708, 0.016962528, 0.018325448, -0.041611,
      -0.0051918817, 0.011049587, 0.009536641, -0.07231649,
      0.03503637, -0.020236874, -0.0017102459, -0.0021461765,
      -0.034633666, 0.07432819, 0.0036866174, -0.05991873,
      -0.010200743, -0.022336228, 0.026324507, 0.0044527748,
      0.024946671, 0.031356413, 0.039175235, -0.060331285,
      0.02872829, 0.11922785, -0.05060712, -0.0031285416,
      0.0933839, 0.047551777, -0.00656914, -0.008723527,
      -0.02056248, -0.07942964, 0.007253245, 0.002748287,
      0.049823694, -0.06911528, -0.08338238, -0.010268196,
      -0.040175784, -0.050169047, -0.03760299, 0.040364724,
      -0.021101788, -0.011530838, 0.008971722, -0.029406672,
      0.02931876, -0.018952321, -0.022184215, 0.020576302,
      -0.04991204, -0.012178673, -0.0012172898, -0.026137197,
      0.0033995172, -0.038044266, 0.023266867, -0.0026854898,
      0.013947766, 0.06699591, 0.0003820753, -0.012578425,
      0.006242479, -0.006871526, -0.01835364, 0.07553381,
      0.032223593, 0.038392317, 0.033943277, -0.015361835,
      0.0023671596, -0.006410763, -0.011273225, 0.043806795,
      0.03606283, -0.021493934, 0.01599088, 0.02685713,
      -0.006905595, 0.032738563, 0.035578374, -0.0017409567,
      0.0049572145, -0.018005563, -0.056904428, 0.05055006,
      0.017217265, -0.032967187, 0.0041171624, -0.047739252,
      0.014147899, -0.0015190738, 0.03499914, 0.015113341,
      -0.0345489, -0.006621507, 0.018658875, 0.017151717,
      0.024052309, 0.015534511, 0.012803335, -0.010520224,
      -0.009986159, -0.025170287, -0.010767526, -0.0331763,
      -0.02887655, 0.018422272, -0.031728882, -0.019984512,
      0.01917353, -0.005411117, 0.029510379, 0.04444927,
      0.04883071, -0.05527611, -0.029397175, 0.0016674862,
      0.03218281, -0.037011594, 0.0133852875, 0.027585778,
      -0.02807942, -0.050464906, -0.030807532, 0.052419852,
      0.043883115, -0.008092162, 0.010648758, 0.018864842,
      -0.015481836, 0.030360516, 0.011446473, -0.012729223,
      -0.023819495, 0.023966925, 0.0020846906, -0.013611769,
      0.0014145249, 0.031439725, 0.003965743, 0.04067084,
      0.017292619, 0.013285721, 0.022078741, 0.016943509,
      -0.005481257, -0.044849746, -0.034649525, -0.007823792,
      0.0045259623, -0.006978939, 0.02072806, 0.015974145,
      0.02982397, -0.027354008, 0.022459835, -0.00072036945,
      -0.037372578, 0.0015904545, -0.018069178, -0.018952165,
      0.0422685, 0.03466362, 0.008375261, -0.045573145,
      -0.01329978, 0.0033290158, -0.04721821, -0.014497412,
      -0.019534541, 0.053129554, 0.016318275, 0.034319974,
      0.015714515, -0.0059726737, 0.01060032, 0.05159713,
      -7.767013e-05, 0.017631222, 0.027890585, -0.010888296,
      -0.04246743, 0.04126155, 0.05201447, -0.0059944508,
      0.00049999217, 0.046713166, 0.020413695, -0.0035533211,
      -0.002710231, 0.042235896, 0.0041315113, 0.010178902,
      0.018899616, -0.037398227, -0.002279069, -0.04831987,
      -0.001163196, -0.03974953, -0.009341693, 0.02349342,
      0.027661255, -0.001237295, -0.09014792, -0.021614574,
      0.058480415, 0.0067279935, -0.03929149, 0.016154243,
      -0.02928018, -0.00096864376, 0.015775573, -0.028529635,
      -0.047811847, 0.03688566, 0.00042255022, 0.006742358,
      0.030198013, 0.007406613, 0.0048276815, -0.006877288,
      0.0096768085, 0.075514235, -0.06486873, -0.0061378893,
      -0.028752165, -0.0019614194, -0.0131959515, -0.02510152,
      -0.051941436, -0.016849462, -0.006709643, 0.025149746,
      -0.041317854, 0.0469566, 0.0034516766, -0.021607826,
      0.021998145, -0.005957742, 0.005200123, -0.01102317,
      -0.020540876, 0.010962356, -0.030201081, 0.01993859,
      0.015492738, 0.007320189, -0.0187165, -0.028290724,
      -0.027129764, -0.02083135, 0.017367607, 0.012497472,
      0.0030506367, -0.0082753375, 0.02891801, 0.0068478985,
      -0.041926373, 0.02490503, -0.021034969, -0.02723763,
      0.001976495, 0.038743537, 0.013416873, 0.011570836,
      -0.013950692, 0.06936353, -0.019110834, -0.006797315,
      0.01770189, -0.028987825, 0.032274004, 0.03258102,
      0.009061344, -0.048655108, -0.019024234, -0.009230033,
      -0.0009142374, -0.0061726947, -0.02224859, -0.022746678,
      0.041500404, -0.009143851, -0.007514959, 0.04656967,
      0.014740103, 0.02110038, -0.005354821, 0.04235084,
      0.019603096, 0.034433916, -0.023885744, -0.054362316,
      -0.048329286, -0.0056372513, -0.069168255, 0.0019363606,
      0.043959282, -0.03201273, 0.010604395, -0.0012379063,
      0.029052066, -0.003674963, 0.003093754, -0.046887744,
      -0.009913566, -0.0040074117, -0.038278874, -0.027658634,
      0.024348333, -0.019273352, 0.020900667, 0.015969455,
      -0.003748979, -0.015444004, 0.021196201, 0.017359698,
      -0.0328592, 0.039604686, -0.012260874, 0.019616889,
      0.009941002, -0.019062702, -0.026937624, -0.016166996,
      -0.008572518, -0.030961791, 0.03432116, -0.0046829353,
      0.021838997, 0.0038940362, -0.017426444, 0.009034499,
      0.04260329, -0.01624323, 0.0024023112, 0.032987554,
      -0.020108506, -0.0013330494, -0.020024143, 0.018695356,
      0.07103268, -0.011008666, 0.025988502, 0.039587826,
      -0.009283805, -0.003624476, 0.006226761, -0.009106092,
      0.030290036, -0.010103529, -0.04699319, -0.013131862,
      0.0036870006, -0.012103904, -0.016797582, 0.031351466,
      0.009809818, -0.023984665, 0.017016461, -0.0004174254,
      -0.019784188, -0.039282784, -0.017012462, 0.0024677226,
      0.043809455, 0.010448085, 0.012296574, -0.012149865,
      0.01410708, 0.004191558, 0.0042414255, 0.01867764,
      0.01257571, -0.000968191, 0.01896165, -0.018631807,
      0.048321173, -0.03456341, -0.008584301, 0.049871966,
      4.4712477e-05, -0.0051842546, 0.009433946, -0.002022321,
      0.0119975265, 0.0008314029, 0.012836841, -0.037227444,
      0.0057561626, 0.0018318145, -0.029733421, -0.021884408,
      0.02891508, 0.031947244, 0.050179344, -0.008853268,
      -0.06615851, 0.05702575, -6.2917876e-05, 0.0046332283,
      -0.038259793, -0.04795183, 0.017640445, 0.038597267,
      -0.011200357, -0.010558111, -0.0013135254, 0.023821631,
      -0.0051694587, 0.039094105, 0.007096718, -0.049142253,
      0.024529895, 0.016969625, 0.042778168, 0.033142556,
      -0.01642818, 0.054725572, 0.01995115, -0.04255012,
      0.02272655, -0.033250358, -0.0007877413, 0.038044542,
      -0.03910067, -0.04595184, 0.0034351812, -0.0017456275,
      -0.012710631, 0.06560817, -0.07660452, 0.0145767415,
      -0.04059342, -0.009771855, -0.0021494897, -0.021590762,
      -0.055203445, -0.06060568, 0.009543021, -0.017128214,
      -0.004229073, 0.018024536, -0.027184486, 0.031157276,
      -0.018148933, -0.004901789, -0.01695701, -0.0060262396,
      -0.014977763, -0.0032398459, -0.035223756, 0.034771472,
      0.037969075, 0.0014832692, -0.014489783, -0.0069588823,
      -0.012722205, -0.00458915, -0.029414736, -0.021871215,
      -0.04372976, -0.033005044, -0.0048129964, 0.010000271,
      0.049894728, -0.024773533, -0.0012239289, 0.017137045,
      0.05286919, -0.006752598, 0.00026533374, 0.0043819635,
      -0.008288234, 0.025805423, 0.05019344, 0.042557407,
      0.003980365, 0.01837216, 0.005681638, -0.014770037,
      0.011860068, 0.0061821956, 0.010446275, 0.054390915,
      -0.048860926, -0.023362484, 0.04248164, 0.0052846908,
      0.013714581, -0.005979163, -0.018983567, -0.0048494893,
      0.037415516, -0.017164368, 0.014178913, -0.030414792,
      -0.0045550987, 0.014293121, 0.026650008, 0.007193895,
      -0.00597236, 0.028873011, -0.024326906, -0.0067130416,
      -0.03719356, 0.03968605, -0.0068663764, 0.030116187,
      -0.018795721, 0.008038071, 0.029396333, -0.006554717,
      0.055733718, -0.06483725, -0.015466347, -0.010968109,
      0.027206592, -0.018671397, 0.06375345, 0.025036491,
      -0.02028585, -0.02242114, 0.0042034034, 0.0094353845,
      0.004466486, 0.041735865, -0.013409357, 0.03307471,
      -0.020508781, -0.02030798, 0.05253183, 0.0026669072,
      -0.0139997965, 0.028504651, 0.050344903, 0.014011175,
      -0.009740679, 0.032076947, 0.015503739, 0.040838797,
      -0.038377203, 0.036147222, 0.056498654, -0.030147025,
      -0.0032628628, -0.0023589574, -0.005530896, 0.032406732,
      0.0057708225, -0.029818606, -0.009291837, 0.0074942713,
      0.05276015, -0.004983989, -0.05654342, 0.01586609,
      -0.014840427, -0.0398822, 0.019582408, -0.0027440784,
      0.013502925, 0.037930857, -0.017777424, 0.013971739,
      -0.00017727415, -0.031560726, 0.019609971, 0.036829676,
      -0.018761942, -0.023164809, 0.009144981, 0.007785141,
      -0.0134790465, -0.008871404, -0.0151731465, -6.2507934e-05,
      0.002091446, -0.0057512536, 0.072792426, -0.013379657,
      0.019600114, -0.01280945, 0.015626915, 0.034065224,
      -0.01332805, -0.008942544, 0.002679207, 0.02222212,
      0.018636001, 0.019325238, -0.017778827, 0.005862435,
      -0.00053398416, 0.01629176, -0.028279671, -0.028038654,
      0.02072342, 0.0055510844, 0.009259298, -0.0028955517,
      -0.0040659974, -0.04801138, -0.025913984, 0.0047719385,
      -0.0036642181, -0.00993196, -0.03440938, -0.015244514,
      0.00036954143, -0.013564531, 0.0105898315, -0.016886387,
      -0.033337556, 0.00857894, -0.04084181, 0.0041023465,
      -0.009536127, 0.00068765215, -0.025582867, -0.010344754,
      -0.02643584, 0.0046525747, -0.033704575, -0.011209982,
      0.038056094, -0.008974991, -0.0043085697, -0.005762208,
      -0.01973038, -0.007959836, 0.033727985, -0.012574445,
      0.00046827833, 0.017833613, -0.008251113, -0.015050594,
      -0.005057607, -0.011032446, -0.0023512014, 0.009973158,
      -0.011796005, 0.03115526, 0.012587114, -0.0008241834,
      -0.009088551, 0.017297855, -0.0094978325, 0.0028782613,
      0.0022210781, 0.016729964, -0.009111654, -0.015703833,
      -0.00642873, -0.0226205, -0.05434136, -0.050477874,
      0.042018864, 0.04918672, 0.028952364, -0.009836813,
      0.046014007, 0.012994459, -0.01967289, 0.05149295,
      0.010169357, -0.0087201465, 0.04416694, 0.015322836,
      -0.03291382, -0.012606712, 0.034051936, -0.024307871,
      0.0197936, 0.021955209, -0.0058762496, 0.034200165,
      -0.044295684, -0.030673841, -0.04500588, 0.01614164,
      0.009893649, -0.01895898, -0.05404693, -0.012151528,
      -0.012008143, -0.01613138, -0.00012218455, 0.021890404,
      0.012574206, -0.04317196, -0.021066386, -0.05256788,
      0.016199486, -0.015035085, 0.015841603, 0.006596172,
      0.01720508, -0.004428339, -0.004640541, -0.0065937727,
      0.03499029, -0.024559293, -0.022311855, -0.03356369,
      0.015483212, 0.036328677, -0.0013516652, 0.010204894,
      0.09507036, 0.006116581, -0.013269073, 0.020481965,
      0.0072763395, -0.07412712, -0.01739538, -0.004788662,
      0.015221921, 0.027445411, -0.002569122, -0.02987143,
      -0.03877176, 0.037449263, -0.009902233, -0.020074623,
      -0.0036001005, 0.0032942223, 0.04843471, -0.009523979,
      0.034060594, -0.005608704, -0.058412928, 0.03331245,
      0.011094622, -0.03770946, -0.0046344004, -0.06839157,
      -0.008286434, 0.013617306, 0.031027043, -0.015845291,
      -0.028775671, 0.015468954, -0.016731905, 0.03599057,
      0.019875763, -0.008943496, 0.034153115, -0.042539075,
      0.023944698, -0.053392235, 0.030280298, 0.022363223,
      0.0062345588, 0.01304442, -0.03114079, -0.029427448,
      -0.019642146, 0.030167123, 0.05362991, -0.020446898,
      0.0120556485, -0.072758846, -0.028020427, -0.03130412,
      -0.009430416, 0.025014518, 0.019429695, -0.0025430634,
      -0.0063225166, -0.010665375, -0.0075836913, 0.033121556,
      0.037847873, -0.0041475366, 0.0011870619, 0.01785522,
      0.007736634, 0.010052795, -0.030956762, -0.017469525,
      0.014696014, 0.06450245, 0.0036965034, -0.0031159688,
      0.0038374655, -0.0053733643, -0.016773093, -0.0005650999,
      0.02486951, 0.022129443, -0.00040810622, 0.009344644,
      -0.05777276, 0.0001827606, -0.019074272, -0.024838766,
      -0.024127359, 0.013274908, 0.010313344, 0.015980626,
      0.019969894, -0.0462841, 0.0052604894, 0.03794948,
      0.0058082324, -0.020171931, 0.0672829, -0.023571756,
      0.027607, 0.042083047, 0.01004572, 0.035288006,
      0.009611715, 0.02923988, -0.0075664064, -0.015460792
    ]
  ],
  "total_duration": 36862265453,
  "load_duration": 11394414123,
  "prompt_eval_count": 72
}
```
{: .code-scroll }

You read that right, instead of bloviation, it produces a long list of zero-to-one numbers representing a direction in thousand-or-so-dimensional space.  A list of those vectors could then give me a local semantic search, where a project such as [INTERN](https://github.com/jcolag/intern)---which I admit that I stopped using fairly quickly after developing, because I could use `grep` to find most things without an index---could find anyplace where I wrote about web pages, even if I called it something like a "landing page" as I did above.  A database extension such as [SQLite Vec](https://github.com/asg017/sqlite-vec) could then find the most similar vectors/embeddings, which would likely have the most semantically similar words.

Thinking bigger, the process seems far too slow to keep such a database updated regularly, but operating on full files *should* give me ready access to a list of related files.  For a narrower example than all my notes, I don't know if I would actually *do* it, or whether it would add any value around here, but this could give me the ability to add a short list of "probably related" posts on each post on the blog, for people who find the tags overwhelming.  Again, I don't know if it adds value to have a machine recommend that you spend more time on my website, so don't worry that I "plan to add AI" to the blog (even if only behind the scenes) quite yet, but as an illustration of what this might enable, it might help explain why I see Ollama as a useful tool, even if I don't see any major corporate uses of LLMs as worth much.

This also calls back to my post on the quest for [anti-AI licensing]({% post_url 2024-03-03-ai-licenses %}), where I tried to make the point that, among other things, I don't think that we have a rational basis to oppose the *technology*.  We want to oppose exploitation, especially by people (and organization) who can absolutely afford to compensate everybody for their labor.  In other words, you should group OpenAI with Uber and Amazon, not a student excited about implementing language models.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

I needed to fix the Codeberg plugin, now used---as you can see---widely throughout these posts now.  Somehow, despite quite a bit of testing and actual production use, I released it without a necessary variable.  Therefore, it crashed "sometimes," exactly every programmer's favorite behavior.

## Thorough - JSON Resume Theme

{% codeberg jcolag/jsonresume-theme-thorough %}

I don't know that my résumé theme---which I called "thorough," because it actually makes use of most elements of the source file---will see much modification, honestly.  And the fact that it [lives on NPM](https://www.npmjs.com/package/jsonresume-theme-thorough) for distribution, and Microsoft owns both NPM *and* GitHub, it seems suspiciously like all such work will need to happen on GitHub anyway, but for people who only want to download it and use it locally as I did for a lot of the development, or want to recommend changes, you now have a second spot to get at it.

## Socialite

{% codeberg jcolag/socialite %}

In some ways, this feels like a low-priority project, since the largest chunk of code goes to publishing posts to Cohost using its unofficial API, and Cohost {% sfx sigh %} only exists as memories...and archives, these days.  But it also includes a script to un-shorten links that have passed through link-shorteners for more permanent archives, as well as the post-to-Matrix script that I use all week for announcing blog posts on the [blog's Matrix room](https://matrix.to/#/#entropy-arbitrage:matrix.org).

As such, it too has made it to Codeberg.

## Silver Bat

{% codeberg jcolag/silver-bat-01-seeking-refuge %}

In concert with [revising my novel]({% post_url 2025-09-14-revisit-silver-bat %})---and yes, I *know* that I've hammered on it a lot, but I can't run a proper experiment about selling books if people don't know about it...---I have moved the original Markdown source files over to Codeberg.  Over the course of the year, I'll occasionally update a chapter, so that the final public release will also have the full modern version of the novel.

## Mystic T-Square

{% codeberg jcolag/mystic-t-square %}

It seemed like a good idea to move my games, to the extent that you can call them that, to Codeberg, where I'll more likely see them and remember to fix things.  This made the first.

Right, and through the magic of Codeberg Pages, you can actually already [play **Mystic T-Square**](https://jcolag.codeberg.page/mystic-t-square/), too.  I forgot that I set it up to work that way.

## Chasing Phantoms

{% codeberg jcolag/ChasingPhantoms %}

This makes the second of the games.  And as an HTML page, like **Mystic T-Square** above, you can even [play **Chasing Phantoms**](https://jcolag.codeberg.page/ChasingPhantoms/) already deployed to Codeberg Pages.

If you don't immediately see the point of the game, an invisible box zips around in a circle on the page, with a random radius and angular velocity, and you have the job of clicking it as often as possible.  And sometimes the circle and speed changes.  When you click or when the circle changes, the box appears briefly, letting you better guess the path of the box.

One imagines that modern HTML and CSS would make this significantly cleaner to implement, but I worked with what I had at the time.

## Picture to Nonogram

{% codeberg jcolag/picture-nonogram %}

And this makes the third game, though with this one, you can only [solve the Nonograms on my website](https://john.colagioia.net/nono/), because it needs to generate a separate page with the image data to work.

By the way, in looking in my original notes on the project, copying this repository over reminded me that I created the puzzle-games with the intent of running them on **All Around the News**, my one-year foray into trying to run a media outlet that syndicated Free Culture (or near enough) articles.  I envisioned that as the equivalent of a newspaper's puzzle page, maybe putting it against a page of Free Culture comic strips syndicated from across the web.

And then I never set that up.  Nor could I find ongoing comic strips[^3] under usable licenses.

[^3]:  Free Culture comics do exist, but few of them fit the comic strip format that I envisioned for a relatively normal news publication.  Had people subscribed, I would have put some of that money towards commissioning a couple of three-panel strips.

The best that I can tell from the analytics, almost nobody visited it, and almost none of them followed the link to the donation page, which pointed them to the article's source if they had a donation page, me otherwise.  And I only got a couple of entries in the suggestion box, one from a publisher mildly annoyed that I didn't preserve their tracking tokens, and rest [SURE]({% post_url 2024-02-11-sure %})s "offering" me "content" (never under a useful license) to share on what they all insisted on calling a blog, despite clear author and source credits.  After around a year of that, then, I pulled the plug on the project.

## CPREP

{% codeberg jcolag/cprep-background-generator %}

Writing about the *Silver Bat* book over the past week, it came to mind a couple of times that the diversity of the cast comes from the scripts that I wrote as a forerunner to this character-background generator.

For those unfamiliar with the project, rather than picking ethnicities directly, it picks a random splotch of populated land, weighted by its population density, then uses an old skin-color chart, data on regional names, and more recently data exported from the [CIA World Factbook](https://www.cia.gov/the-world-factbook/) to build a probabilistic person who could live there.  Therefore, it weighs heavily toward places such as China and India, but also might surprise you with somebody from Bermuda or Monaco.

By the way, people have asked me over the years if the project would work for fantasy worlds.  And while you technically could, you'd need to replace all the data.  The repository includes country codes, a world map, the dossiers on countries, names by country, different personality schemes, a population density map, skin tone charts, and probably more, all tuned for a relatively recent Earth.

## Next

Once again, I don't have a plan, but do have a lot of other things to do, so expect this week to get packed full of projects moving to Codeberg.

* * *

**Credits**:  The header image is [Pericles' Funeral Oration](https://commons.wikimedia.org/wiki/File:Discurso_funebre_pericles.PNG) by Philipp Foltz, long in the public domain due to copyright expiration.
