# Russell 2000 — round 1 review notes

Branch `russell-2000-round1` of alexandermou/10k-analyzer. Built by round 1 (Sonnet). **Not merged; schedule.json not updated; Claude artifact not republished.** Delete this file before merging.

## 1. Counts

- Source: iShares IWM holdings CSV, fund holdings as of Nov 09, 2026, downloaded from ishares.com (`latest-holdings.csv`, product 239710). Raw copy kept outside the repo.
- Rows in file: 1976; equity rows: 1970; equity rows located in the United States: 1928.
- Rows dropped as not a real ticker (CVR / escrow / contra / vesting placeholders): 7 — `-` (Arcellx CVR, Verdera Energy x2, Coherus Oncology, OmniAb x2) and `P5N994` (Petrocorp escrow). Dotted tickers shown with a space in the file (`MOG A`, `GEF B`, `CRD A`, `BH A`) were converted to `MOG.A` etc.
- Unique US tickers considered: 1,919. **Already in the library: 649** (by ticker or ALIASES). **New candidates: 1,270.**
- Candidates fetched OK: 1,198 → minus 10 duplicates (see 1b) = **1,188 added** (library 1,619 → **2,807**).
- **Skipped: 72 not built** (see section 2) plus 10 duplicates.

### 1b. Duplicates removed (same CIK) — aliases added to index.html on this branch

- TXCP: same company as TCBI already in library
- BELFA: second share class of BELFB
- BATRA: second share class of BATRK
- LILA: second share class of LILAK
- GLIBA: second share class of GLIBK
- RUSHB: same company as RUSHA already in library
- HOS: same company as HLX already in library
- GEF.B: same company as GEF already in library
- METCB: second share class of METC
- BH.A: second share class of BH
- Note: the library entries for these old tickers still carry the old name/ticker: **HLX** (Helix Energy Solutions renamed itself Hornbeck Offshore Services, ticker HOS, Aug 2026) and **TCBI** (Texas Capital Bancshares, ticker now TXCP). Consider refreshing those names.

## 2. Skipped tickers and reasons

**Foreign filers (20-F / 40-F, no 10-K)** — skipped per the instructions; the library supports 20-F, so you may want them: AMBP (Ardagh Metal Packaging Sa), BRSL (Brightstar Lottery Plc), BULL (Webull Corp Class A), CRML (Critical Metals Corp), DLO (Dlocal Class A), GLOB (Globant), GSM (Ferroglobe Plc), NAT (Nordic American Tankers), NTB (Bank Of Nt Butterfield & Son Ltd), PSFE (Paysafe Ltd), SFL (Sfl), SGHC (Super Group Ltd), STNG (Scorpio Tankers), DRUG (Bright Minds Biosciences)

**No 10-K under the CIK StockAnalysis gives.** Most of these are brand-new CIKs (first EDGAR filing 2024–2026): holding-company reorganizations, spin-offs, IPOs or de-SPACs, so the 10-K is filed under a predecessor CIK or hasn't been filed. Those with a first filing in 2026 are the likeliest **successors worth a second look**: AADX (Applied Aerospace And Defense Inc, first filing 2026-03), ADIG (Adi Global Distribution, first filing 2026-01), ALMR (Alamar Biosciences Inc, first filing 2026-01), AVEX (Aevex Corp Class A, first filing 2025-12), BRUN (Boost Run Inc Class A, first filing 2025-10), BXDC (Blackstone Digital Infrastructure, first filing 2025-12), CLBK (Columbia Financial Inc, first filing 2026-03), COAG (Hemab Therapeutics Holdings Inc, first filing 2026-02), CSQR (Csquare Inc, first filing 2026-03), DMRC (Digimarc, first filing 2026-03), ELMT (Elmet Group, first filing 2025-12), EROC (Erock Inc Class A, first filing 2026-02), GENB (Generate Biomedicines Inc, first filing 2025-12), GMRS (Gmr Solutions Inc Class A, first filing 2025-10), ITG (Itg Class A Inc, first filing 2026-02), KARD (Kardigan Inc, first filing 2026-03), KLRA (Kailera Therapeutics Inc, first filing 2025-12), NVRI (Enviri Corp, first filing 2026-03), REA (Rare Earths Americas, first filing 2025-11), REAX (Real Remax Group, first filing 2026-06), RNA (Atrium Therapeutics Inc, first filing 2025-12), SSMR (Sunshine Silver Mining And Refinin, first filing 2025-10), SUJA (Suja Life Inc Class A, first filing 2025-11), SWMR (Swarmer Inc, first filing 2025-10), XPRO (Expro Ltd, first filing 2026-04).
Others (older CIKs with no 10-K): APMD (Apnimed Inc), AVLN (Avalyn Pharma Inc), FCBM (First Carolina Financial Services), HAWK (Hawkeye Inc), HIFS (Hingham Institution For Savings), HMH (Hmh Holding Inc Class A), LCLN (Lincoln International Inc Class A), LFTO (Liftoff Mobile Inc), LIME (Neutron Holdings Inc), MOBI (Mobia Medical Inc), ODTX (Odyssey Therapeutics Inc), PBLS (Parabilis Medicines Inc), PFBC (Preferred Bank), REF (Reformation), SBMT (Silver Bow Mining Corp), SCTX (Scribe Therapeutics Inc), SPTX (Seaport Therapeutics Inc), TOWN (Townebank), VGNT (Versigent Plc), WHK (Whitehawk Minerals Corp Class A). Note PFBC (Preferred Bank) and TOWN (TowneBank) file with bank regulators, not the SEC.

**Other failures:**
- ADRO (Chinook Therapeutics Inc): HTTP Error 404: Not Found
- AKE (Akero Therapeutics Cvr): HTTP Error 404: Not Found
- FRBA (First Bank): no is column for 10-K period 2014-12-31 (have ['TTM', '2025-12-31', '2024-12-31', '2023-12-31'])
- FUBO (Fubotv Class A): no is column for 10-K period 2024-12-31 (have ['TTM', '2025-09-27', '2024-09-28', '2023-09-30'])
- GTXI (Gtxi Inc - Cvr): HTTP Error 404: Not Found
- INH (Inhibrx Inc Cvr): HTTP Error 404: Not Found
- NBN (Northeast Bank): no is column for 10-K period 2018-06-30 (have ['TTM', '2026-06-30', '2025-06-30', '2024-06-30'])
- PDLI (Pdl Biopharma Inc): HTTP Error 404: Not Found
- PTRN (Pattern Group Series A): 'NoneType' object has no attribute 'group'
- SVIA (Silvia): no prior year
- TSE (Trinseo Plc Prvt): 'NoneType' object has no attribute 'group'
- ZSQR (Z Squared Inc): no is column for 10-K period 2025-12-31 (have ['TTM', '2024-12-31', '2023-12-31'])
- YSWY: no 10-K on EDGAR.

The 10-K-period mismatches (NBN, FRBA, FUBO, ZSQR: StockAnalysis has no annual column for the latest 10-K year; SVIA: no prior year) could be retried by hand. INH/AKE/ADRO/PDLI/GTXI are CVR or acquired-company rows (404), PTRN and TSE are marked private.

## 3. Judgment calls to check

- **Pre-revenue companies (109 built):** StockAnalysis shows no revenue line for these; fetch_sa.py (edited in the tools repo) records revenue as 0 for both years only when every revenue row is empty and the statement has R&D or operating income. Please confirm against each 10-K (grant/collaboration revenue would be a real error): ABOS, ACHV, AIRJ, ALLO, ALXO, ANNX, ANRO, ANTX, AREC, ARTV, AURA, AVBP, AVIR, AVXL, BCAX, BHVN, BNTC, CABA, CADL, CAPR, CELC, CGEM, CLYM, CMPX, CNTN, CNTX, COGT, CRBP, CRVS, CTGO, CTNM, DC, DMAC, DMRA, DNLI, DSGN, DYN, EIKN, ELDN, ELTX, EVEX, FJET, FULC, GALT, GLSI, HYMC, IKT, IMMX, IMRX, IMVT, IRON, JBIO, KYTX, LBRX, LRMR, LTBR, LXEO, MAZE, MBX, MLYS, MNPR, MPLT, NAUT, NB, NERV, NEXT, NGNE, NKTX, NMRA, NNE, NPWR, NVCT, OKUR, OLMA, OMER, ORIC, PALI, PCVX, PPTA, PRAX, RAPP, RCKT, RLMD, RZLT, SABS, SANA, SGMT, SGP, SION, SLDB, SLS, SOC, SPRB, SRRK, SVRA, TARA, TECX, TENX, THRD, TRVI, TYRA, UNCY, USAU, USGO, VERA, VGZ, VOR, ZNTL, ZURA.
- **Descriptions:** all 1,188 are one sentence. 106 are my hand-written rewrites (the rest of the 110 overrides only fix short names); the rest are StockAnalysis's first sentence with the company name swapped for the short name, trailing geography stripped, and banks rewritten as "X is the holding company for Y Bank, which provides banking services to individuals and businesses." **Not verified against filings.** Least sure: PRM (Perimeter), CASK (Sempreon, formerly MGP Ingredients — rename Oct 2026, business may have changed), GPGI (CompoSecure successor; draft says injection molding), NXH (formerly Bed Bath & Beyond), TRON (now a TRX-token treasury company), DMRA, AHRT, XRN, ACH, ASST, RGCO, HPP, STLN.
- **Short names:** descriptive words (Therapeutics, Pharmaceuticals, Technologies …) are dropped only when the result is at least 6 characters or two words and unique; bank/financial words are kept. Skim the picker for odd ones.
- **Segments:** kept for 434 companies (2–7 parts that add up to revenue, no accounting lines, "Other" not the largest, labels ≤45 chars). Dropped for 80. Labels were only lightly tidied automatically; many are geographic.
- **"Debt: None" tiles** are the normal no-borrowings tile (same as 30+ older entries), not a bug.

## 4. Renamed companies (EDGAR former name within the last two years; mentioned in the description)

- ABX Abacus Global Management ← Abacus Life, Inc. (changed 2025-02-04)
- ACH Accendra Health ← Owens & Minor (changed 2025-12-31)
- AHRT AH Realty Trust ← Armada Hoffler Properties, Inc. (changed 2026-02-27)
- ALOY REalloys ← Blackboxstocks (changed 2026-02-25)
- AMCX AMC Global Media ← AMC Networks Inc. (changed 2026-04-03)
- ASST Strive ← Asset Entities Inc. (changed 2025-09-10)
- CASK Sempreon ← MGP Ingredients (changed 2026-10-28)
- CBIO Crescent ← GlycoMimetics (changed 2025-06-23)
- CD Chaince Digital ← Mercurity Fintech Holding Inc. (changed 2025-11-12)
- CDNL Cardinal Infrastructure ← Civil Infrastructure Group Inc. (changed 2025-08-11)
- CHRS Coherus Oncology ← Coherus BioSciences, Inc. (changed 2025-05-28)
- CIFR Cipher Digital ← Cipher Mining Inc. (changed 2026-02-23)
- CMRC Commerce.com ← BigCommerce Holdings, Inc. (changed 2025-07-25)
- CNTN Canton Strategic ← Tharimmune, Inc. (changed 2026-02-11)
- CTEV Claritev ← MultiPlan Corp (changed 2025-02-07)
- CTGO Contango Silver & Gold ← Contango ORE, Inc. (changed 2026-03-30)
- DMRA Damora ← Galecto, Inc. (changed 2026-03-10)
- GLIBK Liberty Capital ← GCI Liberty, Inc. (changed 2026-05-21)
- GOLD Gold.com ← A-Mark Precious Metals, Inc. (changed 2025-12-01)
- GPGI GPGI ← CompoSecure, Inc. (changed 2026-01-21)
- GTN Gray Media ← Gray Television (changed 2025-02-24)
- HAPN Happen ← LendingClub Corp (changed 2026-06-18)
- HUCK Huckleberry.ai ← Domo, Inc. (changed 2026-09-03)
- JBIO Jade Biosciences ← Aerovate Therapeutics, Inc. (changed 2025-04-30)
- KEEL Keel Infrastructure ← Bitfarms Ltd (changed 2026-03-31)
- MAGN Magnera ← Glatfelter Corp (changed 2024-11-04)
- MCHB Mechanics Bank ← HomeStreet, Inc. (changed 2025-08-22)
- MITT TPG Mortgage Investment Trust ← AG Mortgage Investment Trust, Inc. (changed 2025-11-07)
- NAGE Niagen Bioscience ← ChromaDex Corp. (changed 2025-03-10)
- NL NLI ← NL Industries (changed 2026-05-26)
- NPKI NPK International ← Newpark Resources (changed 2024-12-03)
- NRC NRC Health ← National Research (changed 2026-03-27)
- NUAI New Era Energy & Digital ← New Era Helium Inc. (changed 2025-07-29)
- NWPX NWPX Infrastructure ← Northwest Pipe (changed 2025-06-12)
- NXH Neighborhood Intelligence ← Bed Bath & Beyond, Inc. (changed 2026-08-14)
- ONL Orion Properties ← Orion Office REIT Inc. (changed 2025-03-07)
- ONT Onterris ← Montrose Environmental Group, Inc. (changed 2026-04-21)
- OPTU Optimum Communications ← Altice USA, Inc. (changed 2025-11-06)
- OSG Octave Specialty ← Ambac Financial Group (changed 2025-11-10)
- PAMT PAMT ← PAM Transportation Services (changed 2024-11-06)
- PDM Piedmont Realty Trust ← Piedmont Office Realty Trust, Inc. (changed 2025-06-02)
- PLBY Playboy ← PLBY Group, Inc. (changed 2025-06-16)
- POWW Outdoor ← Ammo, Inc. (changed 2025-04-24)
- RDNW RideNow ← RumbleOn, Inc. (changed 2025-08-12)
- RILY BRC Group ← B. Riley Financial, Inc. (changed 2025-12-15)
- RJET Republic Airways ← Mesa Air Group (changed 2025-11-24)
- RPC Ridgepost Capital ← P10, Inc. (changed 2026-02-05)
- SGP SpyGlass ← SpyGlassPharma, Inc. (changed 2025-06-05)
- SHOE Shoe Station ← Shoe Carnival (changed 2026-06-11)
- SRTA Strata Critical Medical ← Blade Air Mobility, Inc. (changed 2025-08-18)
- STLN Starling Oncology ← Oncology Institute, Inc. (changed 2026-08-03)
- STRZ Starz Entertainment ← Lions Gate Entertainment (changed 2025-05-07)
- TDAY USA TODAY ← Gannett Co., Inc. (changed 2025-11-14)
- TE T1 Energy ← FREYR Battery (changed 2025-02-14)
- TIC TIC Solutions ← Acuren (changed 2025-10-07)
- TRON Tron ← SRM Entertainment, Inc. (changed 2025-07-16)
- VISN Vistance Networks ← CommScope Holding Company, Inc. (changed 2026-01-13)
- WHWK Whitehawk ← Aadi Bioscience, Inc. (changed 2025-03-18)
- WYFI WhiteFiber ← White Fiber, Inc. (changed 2025-07-11)
- XMAX XMax ← Nova Lifestyle, Inc. (changed 2025-11-04)
- XRN Chiron Real Estate ← Global Medical REIT Inc. (changed 2026-01-26)
- Shell/SPAC predecessor names (e.g. Queso Holdings, Yellowstone Midco, Roth CH, Churchill Capital Corp X) and cosmetic changes ("Inc.", added/dropped "Pharmaceuticals") were not mentioned. Former *tickers* are not in the data; add aliases in round 2 where you know them (e.g. LC → HAPN, MPLN → CTEV).

## 5. fyLabel set

- AVAH: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- BBW: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Hobby, Toy & Game Shops)
- BGS: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- BXC: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- CAL: fyLabel 2025: company names its fiscal year by the year it starts (period ends Jan 31, 2026); set from my knowledge, please verify
- CRAI: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- CTRN: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Apparel & Accessory Stores)
- CURV: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Apparel & Accessory Stores)
- DBI: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Shoe Stores)
- FOSL: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- GCO: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Shoe Stores)
- HLIO: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- JBI: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- JILL: fyLabel 2025: company names its fiscal year by the year it starts (period ends Jan 31, 2026); set from my knowledge, please verify
- KLC: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- LE: fyLabel 2025: retailer, period ends Jan 30, 2026 (SIC Retail-Family Clothing Stores)
- LOVE: fyLabel 2025: retailer, period ends Feb 01, 2026 (SIC Retail-Furniture Stores)
- NCMI: fyLabel 2025: period ends Jan 01, 2026 (52/53-week year)
- OXM: fyLabel 2025: company names its fiscal year by the year it starts (period ends Jan 31, 2026); set from my knowledge, please verify
- PLAY: fyLabel 2025: retailer, period ends Feb 03, 2026 (SIC Retail-Eating  Places)
- PPIH: fyLabel 2025: company names its fiscal year by the year it starts (period ends Jan 31, 2026); set from my knowledge, please verify
- RCMT: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- RENT: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Retail Stores, NEC)
- SHIM: fyLabel 2025: period ends Jan 02, 2026 (52/53-week year)
- SHOE: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Shoe Stores)
- SVV: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- TITN: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Retail Stores, NEC)
- USNA: fyLabel 2025: period ends Jan 03, 2026 (52/53-week year)
- WLDN: fyLabel 2025: period ends Jan 02, 2026 (52/53-week year)
- WOOF: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Retail Stores, NEC)
- ZUMZ: fyLabel 2025: retailer, period ends Jan 31, 2026 (SIC Retail-Apparel & Accessory Stores)

Left at the calendar year of the period end (Jan-31 year ends, mostly software; **please verify**): AMBA; ASAN; BRZE; CHPT; HUCK; MAMA; MOV; NAVN; NCNO; OOMA; PD; PHR; TTAN; WLTH; YEXT. CAL, OXM, JILL and PPIH were labelled by my knowledge that they name the year by its start; the rest I believe name the year by its end.

## 6. Flags

### 6a. Revenue moved more than 60% year over year (141)

| Ticker | Name | Revenue $M | Prior $M | Change |
|---|---|---:|---:|---:|
| ABAT | American Battery | 21.7 | 4.3 | +407% |
| ABEO | Abeona | 5.8 | 0.0 | new revenue |
| ABUS | Arbutus | 14.1 | 6.2 | +128% |
| ABX | Abacus Global Management | 235.2 | 111.9 | +110% |
| ACHR | Archer Aviation | 0.3 | 0.0 | new revenue |
| ACTG | Acacia Research | 285.2 | 122.3 | +133% |
| AEVA | Aeva Technologies | 18.1 | 9.1 | +100% |
| AKTS | Aktis Oncology | 6.5 | 1.5 | +336% |
| ALEC | Alector | 21.1 | 100.6 | -79% |
| ALMS | Alumis | 24.1 | 0.0 | new revenue |
| ALOY | REalloys | 0.8 | 0.0 | new revenue |
| ALT | Altimmune | 0.0 | 0.0 | +100% |
| AMPX | Amprius | 73.0 | 24.2 | +202% |
| ANAB | AnaptysBio | 234.6 | 91.3 | +157% |
| ARQT | Arcutis | 376.1 | 196.5 | +91% |
| ASMB | Assembly | 72.3 | 28.5 | +154% |
| ASPI | ASP Isotopes | 23.9 | 4.1 | +476% |
| AVBH | Avidbank | 30.9 | 81.2 | -62% |
| AVTX | Avalo Therapeutics | 0.1 | 0.4 | -86% |
| BCRX | BioCryst | 874.8 | 450.7 | +94% |
| BDTX | Black Diamond | 70.0 | 0.0 | new revenue |
| BEAM | Beam Therapeutics | 139.7 | 63.5 | +120% |
| BETA | BETA Technologies | 35.6 | 15.1 | +136% |
| BIOA | BioAge Labs | 9.0 | 0.0 | new revenue |
| BNAI | Brand Engagement Network | 0.3 | 0.1 | +180% |
| BZAI | Blaize | 38.6 | 1.6 | +2392% |
| CAMP | Camp4 Therapeutics | 3.5 | 0.7 | +438% |
| CARL | Carlsmed | 50.5 | 27.2 | +86% |
| CBIO | Crescent | 10.8 | 0.0 | new revenue |
| CD | Chaince Digital | 1.9 | 0.5 | +282% |
| CDZI | Cadiz | 16.3 | 9.6 | +70% |
| CLDX | Celldex | 1.5 | 7.0 | -78% |
| CNTB | Connect | 0.1 | 26.0 | -100% |
| COFS | ChoiceOne Financial Services | 161.4 | 91.7 | +76% |
| CRMD | CorMedix | 311.7 | 43.5 | +617% |
| CRSP | CRISPR | 3.5 | 37.3 | -91% |
| DCTH | Delcath Systems | 85.2 | 37.2 | +129% |
| DEC | Diversified Energy | 1,611.5 | 794.8 | +103% |
| DUOT | Duos Technologies | 27.0 | 7.3 | +271% |
| DX | Dynex Capital | 372.1 | 150.4 | +147% |
| EOSE | Eos Energy Enterprises | 114.2 | 15.6 | +632% |
| EPSN | Epsilon Energy | 51.6 | 31.5 | +64% |
| ETON | Eton Pharmaceuticals | 80.0 | 39.0 | +105% |
| EVMN | Evommune | 13.0 | 7.0 | +86% |
| FBYD | Falcon's Beyond | 14.9 | 6.8 | +121% |
| FDMT | 4D Molecular | 85.2 | 0.0 | +212925% |
| FF | FutureFuel | 95.7 | 243.3 | -61% |
| FINW | FinWise Bancorp | 130.7 | 81.4 | +61% |
| FISI | Financial Institutions | 244.9 | 116.9 | +110% |
| FLY | Firefly Aerospace | 159.8 | 60.8 | +163% |
| GERN | Geron | 183.9 | 77.0 | +139% |
| GEVO | Gevo | 160.6 | 16.9 | +850% |
| GLUE | Monte Rosa | 123.7 | 75.6 | +64% |
| GOGO | Gogo | 910.5 | 444.7 | +105% |
| GOLD | Gold.com | 25,513.4 | 10,978.6 | +132% |
| GPGI | GPGI | 59.8 | 420.6 | -86% |
| HYLN | Hyliion | 3.5 | 1.5 | +130% |
| IA | Innovative Aerosystems | 84.3 | 47.2 | +79% |
| IDR | Idaho Strategic Resources | 42.4 | 25.8 | +65% |
| IDYA | IDEAYA | 218.7 | 7.0 | +3024% |
| INBX | Inhibrx | 1.3 | 0.2 | +550% |
| INV | Innventure | 2.1 | 1.2 | +69% |
| IPSC | Century | 109.2 | 6.6 | +1556% |
| IVVD | Invivyd | 53.4 | 25.4 | +111% |
| JOBY | Joby Aviation | 53.4 | 0.1 | +38057% |
| KEEL | Keel Infrastructure | 229.3 | 133.3 | +72% |
| KREF | KKR Real Estate Finance Trust | 15.8 | 100.6 | -84% |
| KROS | Keros Therapeutics | 244.1 | 3.5 | +6775% |
| KRRO | Korro Bio | 6.4 | 2.3 | +181% |
| LCID | Lucid | 1,353.8 | 807.8 | +68% |
| LENZ | LENZ Therapeutics | 19.1 | 0.0 | new revenue |
| LPTH | LightPath | 71.7 | 37.2 | +93% |
| LWLG | Lightwave Logic | 0.2 | 0.1 | +140% |
| LXRX | Lexicon | 49.8 | 31.1 | +60% |
| MBI | MBIA | 97.0 | 27.0 | +259% |
| MCHB | Mechanics Bank | 663.2 | 380.1 | +74% |
| MGTX | MeiraGTx | 81.4 | 33.3 | +145% |
| MLP | Maui Land & Pineapple | 19.5 | 11.6 | +68% |
| NREF | NexPoint Real Estate Finance | 157.3 | 73.1 | +115% |
| NRGV | Energy Vault | 203.7 | 46.2 | +341% |
| NUAI | New Era Energy & Digital | 0.9 | 0.5 | +68% |
| NUTX | Nutex Health | 875.3 | 479.9 | +82% |
| NUVB | Nuvation Bio | 62.9 | 7.9 | +699% |
| NVAX | Novavax | 1,123.5 | 682.2 | +65% |
| NWFL | Norwood Financial | 87.9 | 51.0 | +72% |
| OBIO | Orchestra BioMed | 33.5 | 2.6 | +1168% |
| ONDS | Ondas | 50.7 | 7.2 | +606% |
| ORC | Orchid Island Capital | 179.5 | 54.4 | +230% |
| ORMP | Oramed | 2.0 | 0.0 | new revenue |
| OVID | Ovid Therapeutics | 7.2 | 0.6 | +1172% |
| PAL | Proficient Auto Logistics | 430.4 | 240.8 | +79% |
| PCT | PureCycle | 8.4 | 0.0 | new revenue |
| PFSI | PennyMac Financial Services | 3,462.1 | 2,026.0 | +71% |
| PGEN | Precigen | 9.7 | 3.9 | +147% |
| PHAT | Phathom | 175.1 | 55.2 | +217% |
| PRLD | Prelude | 12.1 | 7.0 | +73% |
| PROK | ProKidney | 0.9 | 0.1 | +1012% |
| PRTA | Prothena | 9.7 | 135.2 | -93% |
| QBTS | D-Wave Quantum | 24.6 | 8.8 | +178% |
| QUBT | Quantum Computing | 0.7 | 0.4 | +84% |
| RBKB | Rhinebeck Bancorp | 53.4 | 28.7 | +86% |
| RCAT | Red Cat | 40.7 | 7.3 | +459% |
| RGNX | REGENXBIO | 170.4 | 83.3 | +105% |
| RIGL | Rigel Pharmaceuticals | 294.3 | 179.3 | +64% |
| RIOT | Riot Platforms | 647.4 | 376.7 | +72% |
| RNAC | Cartesian | 2.8 | 38.9 | -93% |
| SBET | Sharplink | 28.1 | 3.7 | +666% |
| SEG | Seaport Entertainment | 132.8 | 78.1 | +70% |
| SES | SES AI | 21.0 | 2.0 | +929% |
| SHAZ | SharonAI | 1.6 | 0.4 | +257% |
| SKYH | Sky Harbour | 27.5 | 14.8 | +87% |
| SNDX | Syndax | 172.3 | 23.7 | +628% |
| SOUN | SoundHound AI | 168.9 | 84.7 | +99% |
| SPCE | Virgin Galactic | 1.5 | 7.0 | -78% |
| SRZN | Surrozen | 3.5 | 10.7 | -67% |
| STOK | Stoke Therapeutics | 184.4 | 36.5 | +405% |
| STRO | Sutro Biopharma | 102.5 | 62.0 | +65% |
| STTK | Shattuck Labs | 1.0 | 5.7 | -83% |
| TARS | Tarsus | 451.4 | 182.9 | +147% |
| TE | T1 Energy | 755.3 | 2.9 | +25590% |
| TRDA | Entrada Therapeutics | 25.4 | 210.8 | -88% |
| TSSI | TSS | 245.7 | 148.1 | +66% |
| TTGT | TechTarget | 486.8 | 284.9 | +71% |
| TVTX | Travere | 490.7 | 233.2 | +110% |
| TYGO | Tigo Energy | 103.5 | 54.0 | +92% |
| UAMY | United States Antimony | 39.3 | 14.9 | +163% |
| UMAC | Unusual Machines | 11.2 | 5.6 | +101% |
| USAR | USA Rare Earth | 1.6 | 0.0 | new revenue |
| VRDN | Viridian | 70.8 | 0.3 | +23517% |
| VSTM | Verastem | 30.9 | 10.0 | +209% |
| WASH | Washington Trust Bancorp | 229.1 | 100.7 | +128% |
| WATT | Energous | 5.6 | 0.8 | +631% |
| WHWK | Whitehawk | 7.1 | 26.0 | -73% |
| WVE | Wave Life Sciences | 42.7 | 108.3 | -61% |
| WYFI | WhiteFiber | 77.7 | 47.1 | +65% |
| XENE | Xenon Pharmaceuticals | 7.5 | 0.0 | new revenue |
| XFOR | X4 Pharmaceuticals | 35.1 | 2.6 | +1271% |
| XMAX | XMax | 16.7 | 9.7 | +73% |
| XZO | Exzeo | 221.3 | 134.5 | +65% |
| ZBIO | Zenas BioPharma | 10.0 | 5.0 | +100% |
| ZVRA | Zevra Therapeutics | 106.5 | 23.6 | +351% |

### 6b. Net margin above +60% or below −60% (219; pre-revenue companies excluded)

| Ticker | Name | Revenue $M | Net income $M | Margin |
|---|---|---:|---:|---:|
| ABAT | American Battery | 21.7 | -73.4 | -338% |
| ABEO | Abeona | 5.8 | 71.2 | +1223% |
| ABSI | Absci | 2.8 | -115.2 | -4114% |
| ABUS | Arbutus | 14.1 | -33.5 | -238% |
| ACHR | Archer Aviation | 0.3 | -618.2 | -206067% |
| ACRS | Aclaris | 7.8 | -64.9 | -829% |
| ADCT | ADC Therapeutics | 81.4 | -142.6 | -175% |
| AEVA | Aeva Technologies | 18.1 | -145.4 | -804% |
| AGIO | Agios Pharmaceuticals | 54.0 | -412.8 | -764% |
| AI | C3.ai | 250.3 | -470.4 | -188% |
| AKTS | Aktis Oncology | 6.5 | -63.7 | -980% |
| ALCO | Alico | 44.1 | -147.3 | -334% |
| ALEC | Alector | 21.1 | -142.9 | -679% |
| ALMS | Alumis | 24.1 | -243.3 | -1012% |
| ALMU | Aeluma | 4.5 | -9.2 | -205% |
| ALOY | REalloys | 0.8 | -75.6 | -9445% |
| ALT | Altimmune | 0.0 | -88.1 | -220225% |
| ALTI | AlTi Global | 255.0 | -153.7 | -60% |
| AMPX | Amprius | 73.0 | -44.0 | -60% |
| AOMR | Angel Oak Mortgage REIT | 61.0 | 43.9 | +72% |
| AQST | Aquestive | 44.5 | -83.8 | -188% |
| ARCT | Arcturus | 82.0 | -65.8 | -80% |
| ARMP | Armata | 4.9 | -173.8 | -3547% |
| ARX | Accelerant | 856.3 | -1,425.0 | -166% |
| ASPI | ASP Isotopes | 23.9 | -175.1 | -734% |
| ASPN | Aspen Aerogels | 271.1 | -389.6 | -144% |
| ASST | Strive | 5.7 | -424.9 | -7416% |
| ATEX | Anterix | 6.5 | 90.6 | +1394% |
| ATOM | Atomera | 0.1 | -20.2 | -28814% |
| AUPH | Aurinia | 283.1 | 287.2 | +101% |
| AVBH | Avidbank | 30.9 | -19.6 | -63% |
| AVR | Anteris Technologies | 1.9 | -94.1 | -4929% |
| AVTX | Avalo Therapeutics | 0.1 | -78.3 | -130433% |
| BBAI | BigBear.ai | 127.7 | -293.9 | -230% |
| BBNX | Beta Bionics | 100.2 | -73.2 | -73% |
| BETA | BETA Technologies | 35.6 | -963.2 | -2704% |
| BETR | Better Home & Finance | 164.9 | -165.9 | -101% |
| BFLY | Butterfly Network | 97.6 | -77.1 | -79% |
| BIOA | BioAge Labs | 9.0 | -80.6 | -897% |
| BKSY | BlackSky | 106.6 | -70.3 | -66% |
| BMBL | Bumble | 965.7 | -655.5 | -68% |
| BMRC | Bank of Marin Bancorp | 29.1 | -35.7 | -123% |
| BNAI | Brand Engagement Network | 0.3 | -8.6 | -3079% |
| BTBT | Bit Digital | 112.1 | -80.3 | -72% |
| BZAI | Blaize | 38.6 | -206.9 | -536% |
| CAMP | Camp4 Therapeutics | 3.5 | -80.4 | -2297% |
| CATX | Perspective | 0.9 | -103.1 | -11718% |
| CBIO | Crescent | 10.8 | -153.9 | -1420% |
| CCCC | C4 Therapeutics | 36.0 | -105.0 | -292% |
| CD | Chaince Digital | 1.9 | -5.1 | -273% |
| CDXS | Codexis | 70.4 | -44.0 | -62% |
| CDZI | Cadiz | 16.3 | -39.2 | -241% |
| CHRS | Coherus Oncology | 42.2 | 168.0 | +398% |
| CIFR | Cipher Digital | 223.9 | -822.2 | -367% |
| CLDX | Celldex | 1.5 | -258.8 | -16803% |
| CLPT | ClearPoint Neuro | 37.0 | -25.5 | -69% |
| CNNE | Cannae | 423.6 | -513.2 | -121% |
| CNTB | Connect | 0.1 | -55.5 | -92467% |
| CORZ | Core Scientific | 319.0 | -280.7 | -88% |
| CRBU | Caribou | 11.2 | -148.1 | -1327% |
| CRSP | CRISPR | 3.5 | -581.6 | -16570% |
| CV | CapsoVision | 13.6 | -25.3 | -187% |
| CVRX | CVRx | 56.6 | -53.3 | -94% |
| DJCO | Daily Journal | 87.7 | 112.1 | +128% |
| DJT | Trump Media | 3.7 | -712.1 | -19349% |
| DNA | Ginkgo Bioworks | 170.2 | -312.8 | -184% |
| DTIL | Precision | 34.3 | -45.7 | -133% |
| DX | Dynex Capital | 372.1 | 308.9 | +83% |
| EDIT | Editas Medicine | 40.5 | -160.1 | -395% |
| ENTA | Enanta | 65.3 | -81.9 | -125% |
| ENVX | Enovix | 31.8 | -156.7 | -493% |
| EOSE | Eos Energy Enterprises | 114.2 | -1,744.8 | -1528% |
| EU | enCore Energy | 43.2 | -56.9 | -132% |
| EVMN | Evommune | 13.0 | -68.9 | -530% |
| EYPT | EyePoint | 31.4 | -232.0 | -739% |
| FCEL | FuelCell Energy | 158.2 | -191.1 | -121% |
| FDMT | 4D Molecular | 85.2 | -140.1 | -164% |
| FGBI | First Guaranty Bancshares | 95.4 | -58.4 | -61% |
| FHTX | Foghorn | 30.9 | -74.3 | -240% |
| FLY | Firefly Aerospace | 159.8 | -334.0 | -209% |
| FWDI | Forward Industries | 18.2 | -167.0 | -918% |
| GEMI | Gemini Space Station | 179.6 | -582.8 | -325% |
| GPGI | GPGI | 59.8 | -136.0 | -227% |
| GRAL | GRAIL | 147.2 | -408.4 | -277% |
| HPP | Hudson Pacific Properties | 831.0 | -572.2 | -69% |
| HUT | Hut 8 | 235.1 | -225.4 | -96% |
| HYLN | Hyliion | 3.5 | -57.2 | -1643% |
| HYPR | Hyperfine | 13.6 | -35.6 | -262% |
| IE | Ivanhoe Electric | 3.2 | -105.9 | -3268% |
| IMNM | Immunome | 6.9 | -212.4 | -3060% |
| INBX | Inhibrx | 1.3 | -140.1 | -10774% |
| INDI | indie Semiconductor | 217.4 | -143.1 | -66% |
| INFQ | Infleqtion | 32.5 | -31.8 | -98% |
| INV | Innventure | 2.1 | -293.4 | -14245% |
| IRD | Opus Genetics | 14.2 | -49.6 | -349% |
| IVR | Invesco Mortgage Capital | 119.8 | 88.2 | +74% |
| IVVD | Invivyd | 53.4 | -52.5 | -98% |
| JANX | Janux Therapeutics | 10.0 | -113.6 | -1136% |
| JOBY | Joby Aviation | 53.4 | -929.8 | -1741% |
| KEEL | Keel Infrastructure | 229.3 | -284.5 | -124% |
| KMTS | Kestra Medical | 95.1 | -131.6 | -138% |
| KREF | KKR Real Estate Finance Trust | 15.8 | -69.9 | -441% |
| KRRO | Korro Bio | 6.4 | -117.3 | -1835% |
| KURA | Kura Oncology | 67.5 | -278.7 | -413% |
| LCID | Lucid | 1,353.8 | -3,681.7 | -272% |
| LCTX | Lineage Cell | 14.6 | -63.5 | -436% |
| LENZ | LENZ Therapeutics | 19.1 | -82.1 | -430% |
| LODE | Comstock Inc. | 1.6 | -43.1 | -2779% |
| LUCD | Lucid Diagnostics | 4.7 | -70.6 | -1498% |
| LVWR | LiveWire | 25.7 | -75.1 | -293% |
| LWLG | Lightwave Logic | 0.2 | -20.3 | -8462% |
| LXRX | Lexicon | 49.8 | -50.3 | -101% |
| LYEL | Lyell Immunopharma | 0.0 | -274.4 | -686125% |
| MBI | MBIA | 97.0 | -177.0 | -182% |
| MGTX | MeiraGTx | 81.4 | -114.2 | -140% |
| MRVI | Maravai LifeSciences | 185.7 | -130.8 | -70% |
| NKTR | Nektar | 55.2 | -164.1 | -297% |
| NLOP | Net Lease Office Properties | 105.9 | -145.3 | -137% |
| NN | NextNav | 4.6 | -189.2 | -4141% |
| NRIX | Nurix Therapeutics | 84.0 | -264.5 | -315% |
| NTLA | Intellia | 67.7 | -412.7 | -610% |
| NUAI | New Era Energy & Digital | 0.9 | -29.6 | -3325% |
| NUVB | Nuvation Bio | 62.9 | -204.6 | -325% |
| NVTS | Navitas Semiconductor | 45.9 | -117.0 | -255% |
| NXDT | NexPoint Diversified Real Estate Trust | 84.7 | -130.2 | -154% |
| OABI | OmniAb | 18.7 | -64.8 | -347% |
| OBIO | Orchestra BioMed | 33.5 | -53.0 | -158% |
| OCGN | Ocugen | 4.4 | -67.8 | -1539% |
| OCUL | Ocular Therapeutix | 52.0 | -265.9 | -512% |
| ONDS | Ondas | 50.7 | -137.2 | -270% |
| ONL | Orion Properties | 135.8 | -139.3 | -103% |
| ORC | Orchid Island Capital | 179.5 | 159.0 | +89% |
| ORMP | Oramed | 2.0 | 63.2 | +3162% |
| OSG | Octave Specialty | 251.2 | -279.9 | -111% |
| OVID | Ovid Therapeutics | 7.2 | -17.1 | -236% |
| PACB | Pacific Biosciences of California | 160.0 | -546.4 | -341% |
| PCT | PureCycle | 8.4 | -182.6 | -2184% |
| PDYN | Palladyne AI | 5.2 | 10.0 | +191% |
| PGEN | Precigen | 9.7 | -429.6 | -4438% |
| PHAT | Phathom | 175.1 | -221.2 | -126% |
| PLUG | Plug Power | 709.9 | -1,631.6 | -230% |
| PRLD | Prelude | 12.1 | -99.5 | -820% |
| PRME | Prime Medicine | 4.6 | -201.1 | -4344% |
| PROK | ProKidney | 0.9 | -69.0 | -7752% |
| PRTA | Prothena | 9.7 | -244.1 | -2522% |
| PSNL | Personalis | 69.7 | -81.3 | -117% |
| QBTS | D-Wave Quantum | 24.6 | -355.1 | -1444% |
| QTRX | Quanterix | 138.9 | -107.2 | -77% |
| QUBT | Quantum Computing | 0.7 | -18.7 | -2746% |
| QUIK | QuickLogic | 13.8 | -14.8 | -108% |
| RARE | Ultragenyx Pharmaceutical | 673.0 | -575.0 | -85% |
| RCAT | Red Cat | 40.7 | -72.1 | -177% |
| RDW | Redwire | 335.4 | -272.3 | -81% |
| REFI | Chicago Atlantic Real Estate Finance | 54.7 | 36.0 | +66% |
| RGNX | REGENXBIO | 170.4 | -193.9 | -114% |
| RGTI | Rigetti Computing | 7.1 | -216.2 | -3050% |
| RIG | Transocean | 3,965.0 | -2,915.0 | -74% |
| RIGL | Rigel Pharmaceuticals | 294.3 | 367.0 | +125% |
| RIOT | Riot Platforms | 647.4 | -663.2 | -102% |
| RNAC | Cartesian | 2.8 | -130.3 | -4654% |
| RPAY | Repay | 309.3 | -256.7 | -83% |
| RR | Richtech Robotics | 5.0 | -15.8 | -312% |
| RUM | RUM | 100.6 | -81.8 | -81% |
| RXRX | Recursion | 74.7 | -644.8 | -863% |
| RYTM | Rhythm | 189.8 | -201.9 | -106% |
| SBET | Sharplink | 28.1 | -734.6 | -2619% |
| SEG | Seaport Entertainment | 132.8 | -116.7 | -88% |
| SENS | Senseonics | 35.3 | -69.1 | -196% |
| SERV | Serve Robotics | 2.6 | -101.4 | -3825% |
| SES | SES AI | 21.0 | -73.0 | -348% |
| SHAZ | SharonAI | 1.6 | -39.6 | -2524% |
| SI | Shoulder Innovations | 47.3 | -40.4 | -85% |
| SIDU | Sidus Space | 3.4 | -29.5 | -872% |
| SITC | SITE Centers | 122.9 | 176.2 | +143% |
| SKYH | Sky Harbour | 27.5 | 18.8 | +68% |
| SLDP | Solid Power | 17.9 | -93.4 | -522% |
| SLNH | Soluna | 29.7 | -69.1 | -232% |
| SMR | NuScale Power | 31.5 | -355.8 | -1130% |
| SNDX | Syndax | 172.3 | -285.4 | -166% |
| SPCE | Virgin Galactic | 1.5 | -278.9 | -18111% |
| SPIR | Spire Global | 71.5 | 51.3 | +72% |
| SPRY | ARS Pharmaceuticals | 84.3 | -171.3 | -203% |
| SRZN | Surrozen | 3.5 | -242.0 | -6955% |
| STRO | Sutro Biopharma | 102.5 | -191.1 | -186% |
| STTK | Shattuck Labs | 1.0 | -48.8 | -4881% |
| STUB | StubHub | 1,745.2 | -1,992.4 | -114% |
| STXS | Stereotaxis | 32.4 | -22.9 | -71% |
| SVCO | Silvaco | 63.1 | -41.2 | -65% |
| TLSI | TriSalus Life Sciences | 45.1 | -69.7 | -154% |
| TNXP | Tonix Pharmaceuticals | 13.1 | -124.0 | -946% |
| TRDA | Entrada Therapeutics | 25.4 | -143.8 | -565% |
| TRON | Tron | 4.7 | -16.8 | -355% |
| TSHA | Taysha Gene Therapies | 9.8 | -109.0 | -1116% |
| TTGT | TechTarget | 486.8 | -1,008.3 | -207% |
| UEC | Uranium Energy | 37.2 | -137.3 | -369% |
| UMAC | Unusual Machines | 11.2 | -19.2 | -171% |
| UPB | Upstream Bio | 2.9 | -143.4 | -5033% |
| URG | Ur-Energy | 27.2 | -74.9 | -275% |
| URGN | UroGen | 109.8 | -153.5 | -140% |
| USAR | USA Rare Earth | 1.6 | -324.5 | -19787% |
| VALU | Value Line | 33.5 | 21.6 | +65% |
| VELO | Velo3D | 46.0 | -71.4 | -155% |
| VENU | Venu | 17.9 | -44.3 | -248% |
| VERI | Veritone | 92.2 | -111.7 | -121% |
| VISN | Vistance Networks | 1,931.6 | 2,214.8 | +115% |
| VNDA | Vanda Pharmaceuticals | 216.1 | -220.5 | -102% |
| VOYG | Voyager Technologies | 166.4 | -116.1 | -70% |
| VRDN | Viridian | 70.8 | -281.9 | -398% |
| VSTM | Verastem | 30.9 | -209.5 | -678% |
| VUZI | Vuzix | 6.3 | -32.3 | -514% |
| VYGR | Voyager Therapeutics | 40.4 | -119.7 | -297% |
| WATT | Energous | 5.6 | -9.6 | -170% |
| WHWK | Whitehawk | 7.1 | -20.6 | -289% |
| WVE | Wave Life Sciences | 42.7 | -204.4 | -478% |
| XENE | Xenon Pharmaceuticals | 7.5 | -345.9 | -4612% |
| XFOR | X4 Pharmaceuticals | 35.1 | -79.2 | -226% |
| ZBIO | Zenas BioPharma | 10.0 | -377.7 | -3777% |
| ZVRA | Zevra Therapeutics | 106.5 | 77.6 | +73% |
| ZYME | Zymeworks | 106.0 | -81.1 | -77% |

### 6c. Revenue under $150M (492, of which 109 have zero revenue — see section 3)

| Ticker | Name | Revenue $M | Prior $M | Net income $M |
|---|---|---:|---:|---:|
| ABAT | American Battery | 21.7 | 4.3 | -73.4 |
| ABEO | Abeona | 5.8 | 0.0 | 71.2 |
| ABSI | Absci | 2.8 | 4.5 | -115.2 |
| ABUS | Arbutus | 14.1 | 6.2 | -33.5 |
| ACHR | Archer Aviation | 0.3 | 0.0 | -618.2 |
| ACR | ACRES Commercial Realty | 87.7 | 78.7 | 0.2 |
| ACRE | Ares Commercial Real Estate | 72.7 | 87.8 | -0.9 |
| ACRS | Aclaris | 7.8 | 18.7 | -64.9 |
| ADCT | ADC Therapeutics | 81.4 | 70.8 | -142.6 |
| AEHR | Aehr Test Systems | 50.0 | 59.0 | -7.1 |
| AEVA | Aeva Technologies | 18.1 | 9.1 | -145.4 |
| AGEN | Agenus | 114.2 | 103.5 | -0.1 |
| AGIO | Agios Pharmaceuticals | 54.0 | 36.5 | -412.8 |
| AIP | Arteris | 70.6 | 57.7 | -34.8 |
| AIRO | AIRO | 90.9 | 86.9 | -4.1 |
| AKTS | Aktis Oncology | 6.5 | 1.5 | -63.7 |
| ALCO | Alico | 44.1 | 46.6 | -147.3 |
| ALEC | Alector | 21.1 | 100.6 | -142.9 |
| ALMS | Alumis | 24.1 | 0.0 | -243.3 |
| ALMU | Aeluma | 4.5 | 4.7 | -9.2 |
| ALOY | REalloys | 0.8 | 0.0 | -75.6 |
| ALT | Altimmune | 0.0 | 0.0 | -88.1 |
| AMBQ | Ambiq Micro | 72.5 | 76.1 | -36.5 |
| AMPX | Amprius | 73.0 | 24.2 | -44.0 |
| ANIK | Anika Therapeutics | 112.8 | 119.9 | -10.9 |
| AOMR | Angel Oak Mortgage REIT | 61.0 | 51.5 | 43.9 |
| AQST | Aquestive | 44.5 | 57.6 | -83.8 |
| ARCT | Arcturus | 82.0 | 152.3 | -65.8 |
| ARL | American Realty Investors | 50.1 | 48.8 | 15.7 |
| ARMP | Armata | 4.9 | 5.2 | -173.8 |
| ASMB | Assembly | 72.3 | 28.5 | -6.1 |
| ASPI | ASP Isotopes | 23.9 | 4.1 | -175.1 |
| ASST | Strive | 5.7 | 3.6 | -424.9 |
| ASUR | Asure Software | 140.5 | 119.8 | -13.1 |
| ASYS | Amtech Systems | 79.4 | 101.2 | -30.3 |
| ATEX | Anterix | 6.5 | 6.0 | 90.6 |
| ATLO | Ames National | 66.1 | 54.0 | 19.0 |
| ATOM | Atomera | 0.1 | 0.1 | -20.2 |
| AVBC | Avidia Bancorp | 103.6 | 90.3 | -3.3 |
| AVBH | Avidbank | 30.9 | 81.2 | -19.6 |
| AVR | Anteris Technologies | 1.9 | 2.7 | -94.1 |
| AVTX | Avalo Therapeutics | 0.1 | 0.4 | -78.3 |
| BBAI | BigBear.ai | 127.7 | 158.2 | -293.9 |
| BBNX | Beta Bionics | 100.2 | 65.1 | -73.2 |
| BCBP | BCB Bancorp | 101.6 | 95.0 | -14.5 |
| BCML | BayCom | 100.5 | 97.5 | 23.9 |
| BDTX | Black Diamond | 70.0 | 0.0 | 22.4 |
| BEAM | Beam Therapeutics | 139.7 | 63.5 | -80.0 |
| BETA | BETA Technologies | 35.6 | 15.1 | -963.2 |
| BFLY | Butterfly Network | 97.6 | 82.1 | -77.1 |
| BIOA | BioAge Labs | 9.0 | 0.0 | -80.6 |
| BKSY | BlackSky | 106.6 | 102.1 | -70.3 |
| BKTI | BK Technologies | 86.1 | 76.6 | 13.5 |
| BLND | Blend Labs | 123.6 | 115.8 | -25.9 |
| BLZE | Backblaze | 145.8 | 127.6 | -25.6 |
| BMRC | Bank of Marin Bancorp | 29.1 | 70.2 | -35.7 |
| BNAI | Brand Engagement Network | 0.3 | 0.1 | -8.6 |
| BOC | Boston Omaha | 114.4 | 108.3 | -12.4 |
| BPRN | Princeton Bancorp | 84.3 | 74.7 | 18.6 |
| BRBS | Blue Ridge Bankshares | 91.7 | 92.2 | 10.7 |
| BRT | BRT Apartments | 96.8 | 97.3 | -11.4 |
| BSVN | Bank7 | 96.4 | 97.5 | 43.1 |
| BTBT | Bit Digital | 112.1 | 107.5 | -80.3 |
| BVFL | BV Financial | 39.6 | 37.7 | 13.5 |
| BWB | Bridgewater Bancshares | 143.3 | 109.6 | 42.0 |
| BWFG | Bankwell Financial | 108.3 | 87.0 | 34.8 |
| BZAI | Blaize | 38.6 | 1.6 | -206.9 |
| CAMP | Camp4 Therapeutics | 3.5 | 0.7 | -80.4 |
| CARL | Carlsmed | 50.5 | 27.2 | -30.2 |
| CATX | Perspective | 0.9 | 1.4 | -103.1 |
| CBAN | Colony Bankcorp | 132.2 | 115.5 | 28.2 |
| CBFV | CB Financial Services | 43.5 | 50.6 | 4.9 |
| CBIO | Crescent | 10.8 | 0.0 | -153.9 |
| CBK | Commercial Bancgroup | 90.4 | 88.5 | 37.2 |
| CBLL | Ceribell | 89.1 | 65.4 | -53.4 |
| CBNA | Chain Bridge Bancorp | 55.0 | 53.0 | 20.2 |
| CCCC | C4 Therapeutics | 36.0 | 35.6 | -105.0 |
| CD | Chaince Digital | 1.9 | 0.5 | -5.1 |
| CDXS | Codexis | 70.4 | 59.3 | -44.0 |
| CDZI | Cadiz | 16.3 | 9.6 | -39.2 |
| CEVA | CEVA | 109.6 | 106.9 | -10.6 |
| CFBK | CF Bankshares | 61.0 | 51.8 | 17.0 |
| CFFI | C&F Financial | 140.8 | 127.3 | 26.8 |
| CHCI | Comstock Holding Companies | 62.9 | 51.3 | 17.1 |
| CHCT | Community Healthcare Trust | 121.2 | 115.8 | 2.1 |
| CHMG | Chemung Financial | 95.1 | 97.3 | 15.1 |
| CHRS | Coherus Oncology | 42.2 | 26.4 | 168.0 |
| CLDX | Celldex | 1.5 | 7.0 | -258.8 |
| CLPT | ClearPoint Neuro | 37.0 | 31.4 | -25.5 |
| CMTV | Community Bancorp | 48.8 | 41.8 | 16.9 |
| CNTB | Connect | 0.1 | 26.0 | -55.5 |
| COSO | CoastalSouth Bancshares | 82.0 | 69.8 | 24.9 |
| CRBU | Caribou | 11.2 | 10.0 | -148.1 |
| CRSP | CRISPR | 3.5 | 37.3 | -581.6 |
| CTMX | CytomX | 76.2 | 138.1 | -20.4 |
| CTO | CTO Realty Growth | 149.5 | 124.5 | 2.6 |
| CURI | CuriosityStream | 71.7 | 51.1 | -6.4 |
| CV | CapsoVision | 13.6 | 11.8 | -25.3 |
| CVRX | CVRx | 56.6 | 51.3 | -53.3 |
| CWBC | Community West Bancshares | 146.5 | 116.8 | 38.2 |
| CWCO | Consolidated Water | 132.1 | 134.0 | 18.3 |
| CXDO | Crexendo | 68.2 | 60.8 | 5.1 |
| CZFS | Citizens Financial Services | 112.3 | 101.9 | 36.6 |
| CZNC | Citizens & Northern | 122.7 | 108.3 | 23.2 |
| CZWI | Citizens Community Bancorp | 62.3 | 56.4 | 14.4 |
| DCTH | Delcath Systems | 85.2 | 37.2 | 2.7 |
| DIBS | 1stdibs.Com | 89.6 | 88.3 | -13.7 |
| DJCO | Daily Journal | 87.7 | 69.9 | 112.1 |
| DJT | Trump Media | 3.7 | 3.6 | -712.1 |
| DTIL | Precision | 34.3 | 68.7 | -45.7 |
| DUOT | Duos Technologies | 27.0 | 7.3 | -9.8 |
| EBMT | Eagle Bancorp Montana | 91.6 | 81.2 | 14.8 |
| ECBK | ECB Bancorp | 33.2 | 26.2 | 7.8 |
| EDIT | Editas Medicine | 40.5 | 32.3 | -160.1 |
| EFSI | Eagle Financial Services | 69.2 | 72.5 | 8.2 |
| EGAN | eGain | 91.1 | 88.4 | 8.9 |
| ELMD | Electromed | 73.8 | 64.0 | 11.3 |
| ENTA | Enanta | 65.3 | 67.6 | -81.9 |
| ENVX | Enovix | 31.8 | 23.1 | -156.7 |
| EOSE | Eos Energy Enterprises | 114.2 | 15.6 | -1,744.8 |
| EPM | Evolution Petroleum | 86.3 | 85.8 | -2.8 |
| EPSN | Epsilon Energy | 51.6 | 31.5 | -5.8 |
| ERII | Energy Recovery | 135.0 | 144.9 | 23.0 |
| ESP | Espey | 46.1 | 44.0 | 11.2 |
| ESQ | Esquire Financial | 146.6 | 124.8 | 50.8 |
| ETON | Eton Pharmaceuticals | 80.0 | 39.0 | -4.6 |
| EU | enCore Energy | 43.2 | 58.3 | -56.9 |
| EVLV | Evolv Technologies | 145.9 | 103.9 | -33.1 |
| EVMN | Evommune | 13.0 | 7.0 | -68.9 |
| EYPT | EyePoint | 31.4 | 43.3 | -232.0 |
| FBLA | FB Bancorp | 52.1 | 46.1 | 1.2 |
| FBYD | Falcon's Beyond | 14.9 | 6.8 | 2.3 |
| FCAP | First Capital | 50.6 | 43.5 | 16.4 |
| FCCO | First Community | 78.8 | 65.9 | 19.2 |
| FDBC | Fidelity D & D Bancorp | 92.9 | 80.9 | 28.2 |
| FDMT | 4D Molecular | 85.2 | 0.0 | -140.1 |
| FEIM | Frequency Electronics | 63.2 | 69.8 | -0.9 |
| FENC | Fennec | 44.6 | 47.5 | -9.7 |
| FF | FutureFuel | 95.7 | 243.3 | -49.4 |
| FGBI | First Guaranty Bancshares | 95.4 | 113.2 | -58.4 |
| FHTX | Foghorn | 30.9 | 22.6 | -74.3 |
| FINW | FinWise Bancorp | 130.7 | 81.4 | 15.4 |
| FMAO | Farmers & Merchants Bancorp | 121.5 | 101.5 | 32.9 |
| FNLC | The First Bancorp | 94.7 | 80.3 | 34.4 |
| FNRN | First Northern Community Bancorp | 73.6 | 70.4 | 21.1 |
| FPI | Farmland Partners | 51.8 | 57.5 | 28.8 |
| FRAF | Franklin Financial Services | 88.8 | 71.2 | 21.2 |
| FRPH | FRP | 33.7 | 30.4 | 3.3 |
| FUNC | First United | 88.7 | 79.8 | 24.5 |
| FVCB | FVCBankcorp | 67.4 | 58.1 | 22.1 |
| FVR | FrontView REIT | 66.8 | 59.9 | -4.4 |
| FWDI | Forward Industries | 18.2 | 20.0 | -167.0 |
| FXNC | First National | 89.9 | 65.9 | 17.7 |
| GBFH | GBank Financial | 76.0 | 62.4 | 20.9 |
| GCBC | Greene County Bancorp | 92.6 | 74.7 | 41.0 |
| GENC | Gencor Industries | 115.4 | 113.2 | 15.7 |
| GLUE | Monte Rosa | 123.7 | 75.6 | -38.6 |
| GPGI | GPGI | 59.8 | 420.6 | -136.0 |
| GRAL | GRAIL | 147.2 | 125.6 | -408.4 |
| GSIT | GSI Technology | 25.1 | 20.5 | -13.2 |
| GWRS | Global Water Resources | 55.8 | 52.7 | 3.0 |
| GYRE | Gyre Therapeutics | 116.6 | 105.8 | 5.0 |
| HBCP | Home Bancorp | 148.7 | 134.9 | 46.1 |
| HNVR | Hanover Bancorp | 73.3 | 68.4 | 7.3 |
| HQI | HireQuest | 30.6 | 34.6 | 6.3 |
| HWBK | Hawthorn Bancshares | 80.3 | 72.9 | 23.8 |
| HYLN | Hyliion | 3.5 | 1.5 | -57.2 |
| HYPR | Hyperfine | 13.6 | 12.9 | -35.6 |
| IA | Innovative Aerosystems | 84.3 | 47.2 | 15.6 |
| IDN | Intellicheck | 22.7 | 20.0 | 1.3 |
| IDR | Idaho Strategic Resources | 42.4 | 25.8 | 16.7 |
| IE | Ivanhoe Electric | 3.2 | 2.9 | -105.9 |
| IMNM | Immunome | 6.9 | 9.0 | -212.4 |
| INBK | First Internet Bancorp | 116.5 | 134.7 | -35.2 |
| INBX | Inhibrx | 1.3 | 0.2 | -140.1 |
| INFQ | Infleqtion | 32.5 | 28.8 | -31.8 |
| INFU | InfuSystem | 143.4 | 134.9 | 6.6 |
| INTT | InTest | 113.8 | 130.7 | -2.5 |
| INV | Innventure | 2.1 | 1.2 | -293.4 |
| IPSC | Century | 109.2 | 6.6 | -9.6 |
| IRD | Opus Genetics | 14.2 | 11.0 | -49.6 |
| IRMD | IRADIMED | 83.8 | 73.2 | 22.5 |
| ISBA | Isabella Bank | 78.5 | 70.4 | 18.9 |
| ISTR | Investar | 89.9 | 79.7 | 21.9 |
| IVR | Invesco Mortgage Capital | 119.8 | 79.4 | 88.2 |
| IVVD | Invivyd | 53.4 | 25.4 | -52.5 |
| JANX | Janux Therapeutics | 10.0 | 10.6 | -113.6 |
| JMSB | John Marshall Bancorp | 62.6 | 53.3 | 21.2 |
| JOBY | Joby Aviation | 53.4 | 0.1 | -929.8 |
| KMTS | Kestra Medical | 95.1 | 59.8 | -131.6 |
| KOPN | Kopin | 39.3 | 50.3 | 2.6 |
| KREF | KKR Real Estate Finance Trust | 15.8 | 100.6 | -69.9 |
| KRMD | KORU Medical Systems | 41.1 | 33.6 | -2.6 |
| KRRO | Korro Bio | 6.4 | 2.3 | -117.3 |
| KURA | Kura Oncology | 67.5 | 53.9 | -278.7 |
| KVHI | KVH Industries | 111.0 | 113.8 | -7.4 |
| KWY | Kingsway | 137.3 | 112.9 | -11.9 |
| LAND | Gladstone Land | 88.3 | 85.2 | -10.5 |
| LARK | Landmark Bancorp | 70.6 | 60.5 | 18.8 |
| LCNB | LCNB | 92.0 | 81.2 | 23.0 |
| LCTX | Lineage Cell | 14.6 | 9.5 | -63.5 |
| LENZ | LENZ Therapeutics | 19.1 | 0.0 | -82.1 |
| LFCR | Lifecore Biomedical | 128.9 | 128.3 | -44.4 |
| LODE | Comstock Inc. | 1.6 | 3.0 | -43.1 |
| LPTH | LightPath | 71.7 | 37.2 | -20.6 |
| LTRX | Lantronix | 120.9 | 122.9 | -4.2 |
| LUCD | Lucid Diagnostics | 4.7 | 4.3 | -70.6 |
| LVWR | LiveWire | 25.7 | 26.6 | -75.1 |
| LWLG | Lightwave Logic | 0.2 | 0.1 | -20.3 |
| LXRX | Lexicon | 49.8 | 31.1 | -50.3 |
| LYEL | Lyell Immunopharma | 0.0 | 0.1 | -274.4 |
| MASS | 908 Devices | 56.2 | 47.8 | 19.5 |
| MBI | MBIA | 97.0 | 27.0 | -177.0 |
| MGNX | MacroGenics | 149.5 | 150.0 | -74.6 |
| MGTX | MeiraGTx | 81.4 | 33.3 | -114.2 |
| MITT | TPG Mortgage Investment Trust | 89.8 | 87.5 | 27.4 |
| MLP | Maui Land & Pineapple | 19.5 | 11.6 | -10.6 |
| MNSB | MainStreet Bancshares | 73.3 | 65.8 | 13.5 |
| MPTI | M-tron Industries | 54.4 | 49.0 | 8.4 |
| MRAM | Everspin | 55.2 | 50.4 | -0.6 |
| MRBK | Meridian | 126.9 | 112.3 | 21.8 |
| MYFW | First Western Financial | 101.9 | 92.0 | 13.2 |
| NAGE | Niagen Bioscience | 129.4 | 99.6 | 17.4 |
| NECB | Northeast Community Bancorp | 104.8 | 105.6 | 44.4 |
| NKSH | National Bankshares | 55.6 | 45.4 | 15.8 |
| NKTR | Nektar | 55.2 | 98.4 | -164.1 |
| NLOP | Net Lease Office Properties | 105.9 | 142.2 | -145.3 |
| NN | NextNav | 4.6 | 5.7 | -189.2 |
| NPCE | NeuroPace | 100.0 | 79.9 | -21.5 |
| NRC | NRC Health | 137.4 | 143.1 | 11.3 |
| NRIX | Nurix Therapeutics | 84.0 | 54.5 | -264.5 |
| NTLA | Intellia | 67.7 | 57.9 | -412.7 |
| NUAI | New Era Energy & Digital | 0.9 | 0.5 | -29.6 |
| NUVB | Nuvation Bio | 62.9 | 7.9 | -204.6 |
| NVEC | NVE | 26.3 | 25.9 | 15.2 |
| NVTS | Navitas Semiconductor | 45.9 | 83.3 | -117.0 |
| NWFL | Norwood Financial | 87.9 | 51.0 | 27.8 |
| NXDT | NexPoint Diversified Real Estate Trust | 84.7 | 83.3 | -130.2 |
| OABI | OmniAb | 18.7 | 26.4 | -64.8 |
| OBIO | Orchestra BioMed | 33.5 | 2.6 | -53.0 |
| OBT | Orange County Bancorp | 127.2 | 107.7 | 41.6 |
| OCGN | Ocugen | 4.4 | 4.0 | -67.8 |
| OCUL | Ocular Therapeutix | 52.0 | 63.7 | -265.9 |
| OFLX | Omega Flex | 98.3 | 101.7 | 14.8 |
| OLP | One Liberty Properties | 97.3 | 90.5 | 24.1 |
| ONDS | Ondas | 50.7 | 7.2 | -137.2 |
| ONL | Orion Properties | 135.8 | 164.1 | -139.3 |
| OPBK | OP Bancorp | 94.7 | 82.0 | 25.6 |
| OPTX | Syntec Optics | 28.1 | 28.4 | -1.8 |
| ORMP | Oramed | 2.0 | 0.0 | 63.2 |
| OSS | One Stop Systems | 32.2 | 24.6 | 5.1 |
| OSUR | OraSure | 115.0 | 185.8 | -68.7 |
| OVBC | Ohio Valley Banc | 66.7 | 62.0 | 15.6 |
| OVID | Ovid Therapeutics | 7.2 | 0.6 | -17.1 |
| OVLY | Oak Valley Bancorp | 81.7 | 76.6 | 23.9 |
| PAYS | Paysign | 82.0 | 58.4 | 7.5 |
| PBFS | Pioneer Bancorp | 96.3 | 86.7 | 20.3 |
| PCB | PCB Bancorp | 115.7 | 99.7 | 36.9 |
| PCT | PureCycle | 8.4 | 0.0 | -182.6 |
| PCYO | Pure Cycle | 26.1 | 28.8 | 13.1 |
| PDEX | Pro-Dex | 77.5 | 66.6 | 13.7 |
| PDLB | Ponce Financial | 109.2 | 83.7 | 27.6 |
| PDYN | Palladyne AI | 5.2 | 7.8 | 10.0 |
| PEBK | Peoples Bancorp of North Carolina | 90.0 | 81.8 | 19.8 |
| PESI | Perma-Fix Environmental Services | 61.7 | 59.1 | -13.8 |
| PGEN | Precigen | 9.7 | 3.9 | -429.6 |
| PINE | Alpine Income Property Trust | 60.5 | 52.2 | -3.2 |
| PKBK | Parke Bancorp | 79.9 | 63.0 | 37.8 |
| PKE | Park Aerospace | 73.3 | 62.0 | 11.3 |
| PLBC | Plumas Bancorp | 98.3 | 82.5 | 29.6 |
| PLBY | Playboy | 120.9 | 116.1 | -12.7 |
| POWW | Outdoor | 51.1 | 44.4 | -6.6 |
| PRLD | Prelude | 12.1 | 7.0 | -99.5 |
| PRME | Prime Medicine | 4.6 | 3.0 | -201.1 |
| PROK | ProKidney | 0.9 | 0.1 | -69.0 |
| PRTA | Prothena | 9.7 | 135.2 | -244.1 |
| PSNL | Personalis | 69.7 | 84.6 | -81.3 |
| PSTL | Postal Realty Trust | 95.8 | 76.4 | 11.5 |
| QBTS | D-Wave Quantum | 24.6 | 8.8 | -355.1 |
| QTRX | Quanterix | 138.9 | 137.4 | -107.2 |
| QUBT | Quantum Computing | 0.7 | 0.4 | -18.7 |
| QUIK | QuickLogic | 13.8 | 19.6 | -14.8 |
| RBB | RBB Bancorp | 124.0 | 114.7 | 31.9 |
| RBKB | Rhinebeck Bancorp | 53.4 | 28.7 | 10.0 |
| RCAT | Red Cat | 40.7 | 7.3 | -72.1 |
| RDVT | Red Violet | 90.2 | 75.2 | 13.2 |
| RDZN | Roadzen | 55.0 | 44.3 | -22.5 |
| REFI | Chicago Atlantic Real Estate Finance | 54.7 | 55.5 | 36.0 |
| RFIL | RF Industries | 80.6 | 64.9 | 0.1 |
| RGCO | RGC Resources | 95.3 | 84.6 | 13.3 |
| RGTI | Rigetti Computing | 7.1 | 10.8 | -216.2 |
| RMBI | Richmond Mutual Bancorporation | 48.9 | 43.5 | 11.6 |
| RNAC | Cartesian | 2.8 | 38.9 | -130.3 |
| RR | Richtech Robotics | 5.0 | 4.2 | -15.8 |
| RRBI | Red River Bancshares | 125.5 | 109.6 | 42.8 |
| RUM | RUM | 100.6 | 95.5 | -81.8 |
| RXRX | Recursion | 74.7 | 58.8 | -644.8 |
| RXST | RxSight | 134.5 | 139.9 | -38.9 |
| SAMG | Silvercrest Asset Management | 125.3 | 123.7 | 4.9 |
| SATL | Satellogic | 17.7 | 12.9 | -4.8 |
| SBET | Sharplink | 28.1 | 3.7 | -734.6 |
| SBT | Sterling Bancorp (Southfield) | 57.5 | 67.8 | 2.1 |
| SEG | Seaport Entertainment | 132.8 | 78.1 | -116.7 |
| SENS | Senseonics | 35.3 | 22.5 | -69.1 |
| SERV | Serve Robotics | 2.6 | 1.8 | -101.4 |
| SES | SES AI | 21.0 | 2.0 | -73.0 |
| SEVN | Seven Hills Realty Trust | 29.2 | 32.2 | 15.2 |
| SFST | Southern First Bancshares | 118.1 | 93.4 | 30.4 |
| SGHT | Sight Sciences | 77.4 | 79.9 | -38.4 |
| SHAZ | SharonAI | 1.6 | 0.4 | -39.6 |
| SI | Shoulder Innovations | 47.3 | 31.6 | -40.4 |
| SIDU | Sidus Space | 3.4 | 4.7 | -29.5 |
| SIGA | SIGA Technologies | 94.6 | 138.7 | 23.3 |
| SITC | SITE Centers | 122.9 | 278.9 | 176.2 |
| SKYH | Sky Harbour | 27.5 | 14.8 | 18.8 |
| SLDP | Solid Power | 17.9 | 20.1 | -93.4 |
| SLNH | Soluna | 29.7 | 38.0 | -69.1 |
| SMID | Smith-Midland | 93.5 | 78.5 | 12.5 |
| SMR | NuScale Power | 31.5 | 37.0 | -355.8 |
| SMTI | Sanara MedTech | 103.1 | 86.7 | -37.6 |
| SPCE | Virgin Galactic | 1.5 | 7.0 | -278.9 |
| SPIR | Spire Global | 71.5 | 110.5 | 51.3 |
| SPOK | Spok | 139.7 | 137.7 | 15.9 |
| SPRY | ARS Pharmaceuticals | 84.3 | 89.2 | -171.3 |
| SRBK | SR Bancorp | 33.5 | 31.8 | 3.4 |
| SRZN | Surrozen | 3.5 | 10.7 | -242.0 |
| STRO | Sutro Biopharma | 102.5 | 62.0 | -191.1 |
| STTK | Shattuck Labs | 1.0 | 5.7 | -48.8 |
| STXS | Stereotaxis | 32.4 | 26.9 | -22.9 |
| SVCO | Silvaco | 63.1 | 59.7 | -41.2 |
| TAYD | Taylor Devices | 41.6 | 46.3 | 8.6 |
| TCI | Transcontinental Realty Investors | 49.1 | 47.8 | 13.8 |
| TKNO | Alpha Teknova | 40.5 | 37.7 | -17.3 |
| TLSI | TriSalus Life Sciences | 45.1 | 29.4 | -69.7 |
| TNXP | Tonix Pharmaceuticals | 13.1 | 10.1 | -124.0 |
| TRAK | ReposiTrak | 23.3 | 22.6 | 7.4 |
| TRC | Tejon Ranch | 49.6 | 41.9 | 0.1 |
| TRDA | Entrada Therapeutics | 25.4 | 210.8 | -143.8 |
| TRON | Tron | 4.7 | 4.3 | -16.8 |
| TRTX | TPG RE Finance Trust | 132.2 | 149.0 | 45.5 |
| TSBK | Timberland Bancorp | 82.5 | 75.3 | 29.2 |
| TSHA | Taysha Gene Therapies | 9.8 | 8.3 | -109.0 |
| TYGO | Tigo Energy | 103.5 | 54.0 | -1.9 |
| UAMY | United States Antimony | 39.3 | 14.9 | -4.3 |
| UEC | Uranium Energy | 37.2 | 66.8 | -137.3 |
| UHT | Universal Health Realty Income Trust | 100.9 | 100.3 | 17.6 |
| UMAC | Unusual Machines | 11.2 | 5.6 | -19.2 |
| UNTY | Unity Bancorp | 131.8 | 107.1 | 58.0 |
| UPB | Upstream Bio | 2.9 | 2.4 | -143.4 |
| URG | Ur-Energy | 27.2 | 33.7 | -74.9 |
| URGN | UroGen | 109.8 | 90.4 | -153.5 |
| USAR | USA Rare Earth | 1.6 | 0.0 | -324.5 |
| USCB | USCB Financial | 90.2 | 82.7 | 26.1 |
| UTMD | Utah Medical Products | 38.5 | 40.9 | 11.3 |
| VABK | Virginia National Bankshares | 57.6 | 53.1 | 19.3 |
| VALU | Value Line | 33.5 | 35.1 | 21.6 |
| VELO | Velo3D | 46.0 | 41.0 | -71.4 |
| VENU | Venu | 17.9 | 17.8 | -44.3 |
| VERI | Veritone | 92.2 | 92.6 | -111.7 |
| VRDN | Viridian | 70.8 | 0.3 | -281.9 |
| VSTM | Verastem | 30.9 | 10.0 | -209.5 |
| VUZI | Vuzix | 6.3 | 5.8 | -32.3 |
| VYGR | Voyager Therapeutics | 40.4 | 80.0 | -119.7 |
| WATT | Energous | 5.6 | 0.8 | -9.6 |
| WHG | Westwood | 97.8 | 94.7 | 7.1 |
| WHWK | Whitehawk | 7.1 | 26.0 | -20.6 |
| WNEB | Western New England Bancorp | 82.6 | 72.7 | 15.3 |
| WSBF | Waterstone Financial | 141.9 | 135.5 | 26.4 |
| WTBA | West Bancorporation | 95.2 | 79.8 | 32.6 |
| WVE | Wave Life Sciences | 42.7 | 108.3 | -204.4 |
| WYFI | WhiteFiber | 77.7 | 47.1 | -24.7 |
| XENE | Xenon Pharmaceuticals | 7.5 | 0.0 | -345.9 |
| XFOR | X4 Pharmaceuticals | 35.1 | 2.6 | -79.2 |
| XMAX | XMax | 16.7 | 9.7 | -3.4 |
| XRN | Chiron Real Estate | 148.1 | 138.8 | -12.1 |
| YORW | The York Water | 77.5 | 75.0 | 20.1 |
| ZBIO | Zenas BioPharma | 10.0 | 5.0 | -377.7 |
| ZVRA | Zevra Therapeutics | 106.5 | 23.6 | 77.6 |
| ZYME | Zymeworks | 106.0 | 76.3 | -81.1 |

Zero-revenue companies: ABOS, ACHV, AIRJ, ALLO, ALXO, ANNX, ANRO, ANTX, AREC, ARTV, AURA, AVBP, AVIR, AVXL, BCAX, BHVN, BNTC, CABA, CADL, CAPR, CELC, CGEM, CLYM, CMPX, CNTN, CNTX, COGT, CRBP, CRVS, CTGO, CTNM, DC, DMAC, DMRA, DNLI, DSGN, DYN, EIKN, ELDN, ELTX, EVEX, FJET, FULC, GALT, GLSI, HYMC, IKT, IMMX, IMRX, IMVT, IRON, JBIO, KYTX, LBRX, LRMR, LTBR, LXEO, MAZE, MBX, MLYS, MNPR, MPLT, NAUT, NB, NERV, NEXT, NGNE, NKTX, NMRA, NNE, NPWR, NVCT, OKUR, OLMA, OMER, ORIC, PALI, PCVX, PPTA, PRAX, RAPP, RCKT, RLMD, RZLT, SABS, SANA, SGMT, SGP, SION, SLDB, SLS, SOC, SPRB, SRRK, SVRA, TARA, TECX, TENX, THRD, TRVI, TYRA, UNCY, USAU, USGO, VERA, VGZ, VOR, ZNTL, ZURA

## 7. Checks run
- `checkbridge.py`: checked 2,807 — all add up.
- `views.py`: 2,807 companies in all four views, `errors: []`.
- Searched the 1,188 new entries for `None`/`nan`/`undefined`/`inf` and lowercase sentence starts: only the intended "Debt: None" tiles.
- Not done: spot-checks against filings, mirror build, schedule.json, artifact.
