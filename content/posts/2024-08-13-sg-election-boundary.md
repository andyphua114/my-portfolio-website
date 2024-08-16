+++
title = 'Decoding Singapore Electoral Boundary'
date = 2024-08-13T20:06:32+08:00
draft = false
summary = "This article examines Singapore's electoral boundary delineation and investigates how boundaries have changed in recent elections through the use of a visualization dashboard. Explore and analyze the shifts in electoral boundaries, their potential impacts on election outcomes, and what can changes can we expect in the upcoming General Election."
tags = [
  "api",
  "python",
  "streamlit",
]
categories = [
  "portfolio"
]
+++

The delineation of electoral boundaries in Singapore, managed by the Electoral Boundaries Review Committee (EBRC), plays a crucial role in shaping the political landscape. While the government asserts that these boundaries are drawn to serve the interests of Singaporeans and ensure fair representation, the process has faced scrutiny, with some critics accusing it of being a form of gerrymandering — a tactic where boundaries are altered to favor certain political outcomes.

I was curious about how exactly had the delineation of electoral boundaries changes across the recent election years. Using the data available on [Singapore's open data portal](https://beta.data.gov.sg/datasets?agencies=Elections+Department+%28ELD%29), such as the electoral boundary for the recent four general election (GE) years in 2006, 2011, 2015 and 2020 as well as the results, I set about building a simple dashboard to visualize the changes. You can access the dashboard here: [https://sg-electionmap.streamlit.app/](https://sg-electionmap.streamlit.app/)

This dashboard allows users to visualize and analyze changes in electoral boundaries across different election years. It provides a tool to explore how shifts in voter distribution and constituency adjustments might impact electoral outcomes. Users can independently assess the implications of boundary changes and draw their own conclusions.

{{< figure src="/images/sg-electoral-overview.png" width="600" alt="Dashboard Overview" caption="An overview of the dashboard" class="markdown-image">}}

My first impression was that it seemed like EBRC the decided to be more precise in delineating electoral boundaries for GE2020. Instead of a broad brush approach for the coastal areas off Singapore, the electoral boundaries for GE2020 conformed quite closely to the geographical land masses, even for our islets. We shall see if this trend continues in the upcoming GE.

# Background and Context

Naturally with the upcoming general election, which has to be called by November 2025, there has been an increased attention on changes to electoral boundaries. Most recently in the Parliament debate, Minister Chan presented the [position](https://www.straitstimes.com/singapore/politics/electoral-boundaries-drawn-to-serve-interests-of-singaporeans-not-political-parties-chan-chun-sing) that electoral boundaries are drawn to serve the interests of Singaporeans and not political parties. The opposition parties, on the other hand, argued that such delineation constitutes a form of gerrymandering.

# Number of Electors per MP

To predict some possible changes to the electoral division boundaries for the upcoming GE, one key factor is the number of electors represented per MP. The current range is set at 20,000 to 38,000 per MP, which was also a [contentious topic debated in Parliament](https://www.channelnewsasia.com/singapore/electoral-boundaries-suggestions-wp-psp-rejected-ebrc-free-political-intervention-4532846).

<style scoped>
table th {
  font-size: 12px; /* Font size for table headers */
}
table {
  font-size: 12px;
  margin: 10px
}
</style>

Initially, I wasn't able to find the changes in number of electors on the ELD website, although I was certain it has been publicised and reported. I eventually found the source - it was actually a [response](https://www.eld.gov.sg/press/2024/Written%20Reply%20to%20PQ%20on%20The%20Overall%20Increase%20or%20Decrease%20in%20The%20Number%20of%20Electors%20in%20Each%20ED%20Based%20on%20The%20Latest%20Revised%20REs%20as%20of%201%20June%202024.pdf) to a parliamentary question on the overall increase or decrease in the number of electors in each electoral division. For ease of reference, I have reproduced the figures below. There are two changes I made: (1) added the number of voters in GE2020; and (2) instead of taking the difference between 1 Sep 2023 (based on last Presidential Election) and 1 Jun 2024 as per the parliamentary response, I took the difference between GE2020 and 1 Jun 2024.

Here are a few key takeaways from the changes in number of electors based on the GE2020 electoral boundaries. These are the areas I will focus on, using the dashboard to visualize and develop my own speculations for the upcoming GE.

- Hong Kah North SMC has exceeded the maximum number of electors per MP, with 38,883 electors. Hence, there will most certainly be changes.
- Ang Mo Kio GRC is also close to the maximum number of electors per MP, with 37,744 electors.
- Pasir Ris-Punggol GRC saw an increase in 13,629 electors, pushing it to 36,037 electors per MP.
- East Coast GRC, being a 5-member GRC, now has a lower number of electors compared to 4-member Sengkang GRCs. EBRC is mindful that GRCs with fewer MPs should not have more electors than GRCs with more MPs. We are also likely to see changes here.

{{< details "Increase or decrease in number of electors" >}}

| Electoral Division | Member | GE2020  |  1 Sep 2023 | 1 Jun 2024 | Difference*      | Electors per MP |
|------------------|----- | ---------|------|--------------|---------------------------------------| ----------------------|
| Aljunied         |  5   | 150,821  |  147,990  | 146,621   | <span style="color:red">-4,200</span> |       29,324          |
| Ang Mo Kio       |  5   | 150,821  |  189,798  | 188,722   | 37,901 |     37,744           |
| Bishan-Toa Payoh  |  4  | 101,220  |  98,585  | 97,686    | <span style="color:red">-3,534</span> |      24,421          |
| Chua Chu Kang   |  4     | 106,632  |  107,938  | 107,629   | 997 |     26,907         |
| East Coast         |  5  | 121,644 |  123,961   | 121,786  | 142 |     24,357        |
| Holland-Bukit Timah |  4  | 114,973   |  118,034  | 118,579   | 3,606 |      29,644        |
| Jalan Besar      |  4    | 107,720  |  105,430  | 104,138   | <span style="color:red">-3,582</span> |     26,034           |
| Jurong           |  5 | 131,058|  131,578  | 130,711    | <span style="color:red">-347</span> |     26,142          |
| Marine Parade     |  5   | 139,622    |  139,258  | 137,814   | <span style="color:red">-1,808</span> |     27,562          |
| Marsiling-Yew Tee  |  4  | 117,077  |  118,483  | 117,965   | 888 |     29,491         |
| Nee Soon         |  5   | 146,902|  150,987   | 150,712    | 3,810 |     30,142          |
| Pasir Ris-Punggol  |  5  | 166,556 |  178,687   | 180,185   | 13,629 |     36,037          |
| Sembawang        |  5  | 147,786  |  155,728   | 155,704   | 7,918 |     31,140          |
| Sengkang         |  4   | 120,100|  122,418  | 124,773   | 4,673 |     31,193         |
| Tampines        |  5   | 151,589 |  160,227  | 164,339    | 12,750 |     32,867          |
| Tanjong Pagar    |  5     | 134,494   |  138,046  | 137,559   | 3,065 |     27,511         |
| West Coast       |  5    | 146,089 |  147,022   | 147,079   | 990 |     29,415          |
| Bukit Batok       |  1   | 29,948  |  30,093   | 29,664    | <span style="color:red">-284</span> |     29,664          |
| Bukit Panjang      |  1    | 35,437 |  34,253    | 33,507   | <span style="color:red">-1,930</span> |     33,507          |
| Hong Kah North    |  1    | 28,046 |  34,360   | 38,883   | 10,837 |     38,883           |
| Hougang         |  1     | 26,432|  26,793   | 29,049    | 2,617 |     29,049         |
| Kebun Bahru      |  1    | 22,623 |  22,300   | 21,929    | <span style="color:red">-694</span> |     21,929         |
| Macpherson       |  1    | 28,513 |  27,436    | 26,737    | <span style="color:red">-1,776</span> |     26,737           |
| Marymount       |  1   | 23,431 |  23,173   | 23,126    | <span style="color:red">-305</span> |     23,126           |
| Mountbatten     |  1     | 24,246 |  26,767    | 26,863   | 2,617 |    26,863           |
| Pioneer        |  1    | 24,653|  24,607  | 25,137   | 484 |     25,137          |
| Potong Pasir   |  1     | 19,731|  28,509    | 31,236    | 11,505 |     31,236           |
| Punggol West    |  1    | 26,587|  27,079    | 26,754    | 167 |     26,754           |
| Radin Mas      |  1     | 24,931|  23,620    | 22,867   | <span style="color:red">-2,064</span> |     22,867           |
| Yio Chu Kang   |  1     | 25,962 |  25,430    | 24,948   | <span style="color:red">-1,014</span> |     24,948           |
| Yuhua        |  1    | 21,351|  20,817   | 20,349   | <span style="color:red">-1,002</span> |     20,349           |
| Total        |  93     | 2,651,435|  2,709,407   | 2,713,051   | 61,616 |   29,172    |

<p style="font-size: 12px; ">*Difference in number of electors between GE2020 and 1 Jun 2024</p>

{{< /details >}}

# Changes due to Close Vote Margins?

During the debate, as reported in [The Straits Times](https://www.straitstimes.com/singapore/politics/electoral-boundaries-drawn-to-serve-interests-of-singaporeans-not-political-parties-chan-chun-sing), "opposition MPs raised examples of previous boundary changes to constituencies with close vote margins as instances of gerrymandering. Mr Singh cited how Braddell Heights SMC was incorporated into Marine Parade GRC in 1997, Joo Chiat SMC was merged into Marine Parade GRC in 2015, and three single seats “where the PAP had their smallest percentage of wins” in the 2015 General Election – Fengshan, Sengkang West and Punggol East – became part of group representation constituencies in 2020". 

So is this true?

{{< figure src="/images/sg-electoral-joo-chiat.png" width="800" alt="Joo Chiat" caption="Joo Chiat SMC absorbed into Marine Parade GRC in 2015" class="markdown-image">}}

Joo Chiat SMC was absorbed into Marine Parade GRC in GE2015, after PAP narrowly edged out WP with 9,666 (51%) votes against 9,278 votes (49%) in GE2011. This also led to the creation of Macpherson SMC in GE2015. Indeed, victory by the slightest of margin here.

{{< figure src="/images/sg-electoral-fengshan.png" width="800" alt="Fengshan" caption="Fengshan SMC absorbed into East Coast GRC in 2020" class="markdown-image">}}

Fengshan SMC was absorbed into East Coast GRC in GE2020. PAP secured the SMC with a vote of 12,417 (57.5%) against WP vote count of 9,176 (42.5%) in GE2015. So, not the tightest of vote margin here.

{{< figure src="/images/sg-electoral-skw.png" width="800" alt="Sengkang West" caption="Parts of Sengkang West SMC absorbed into Ang Mo Kio GRC in 2020" class="markdown-image">}}

{{< figure src="/images/sg-electoral-sk.png" width="800" alt="Sengkang" caption="Parts of Sengkang West SMC and Punggol East SMC, together with parts of Pasir Ris-Punggol GRC formed the new Sengkang GRC in 2020" class="markdown-image">}}

In GE2015, PAP secured 17,586 (62.1%) of votes in Sengkang West SMC and 16,977 (51.8%) of votes in Punggol East SMC. Close vote margin? True for Punggol East, not so for Sengkang West. Eventually the vote margin for Sengkang GRC in GE2020 came in close, where WP secured victory with 60,217 votes (52.1%).

Close vote margins? Some yes, some no. So changes due to close vote margins? Maybe.

# Key Areas to Watch for Upcoming GE

As an armchair observer, I humbly refer you to expert opinions from other sources, such as this [article from The Straits Times](https://www.straitstimes.com/singapore/politics/how-might-s-pore-s-electoral-boundaries-be-redrawn-as-several-constituencies-see-a-jump-in-voter-numbers). But allow me to indulge in my own speculation for the fun of it.

### Hong Kah SMC

There will most certainly be changes to Hong Kah North SMC boundary, given that it has exceeded the maximum number of electors per MP, with 38,883 electors. Hong Kah North SMC was originally part of the Hong Kah GRC in GE2006, before becoming an SMC in GE2011.

{{< figure src="/images/sg-electoral-hongkah.png" width="800" alt="Hong Kah" caption="In GE2011, parts of Hong Kah GRC splitted out to form Hong Kah North SMC, with the remaining redesignated as Chua Chu Kang GRC" class="markdown-image">}}

There were no boundary changes for Hong Kah North in GE2015. Notable changes occurred in GE2020: Hong Kah North traded parts with Chua Chu Kang GRC, and some parts were absorbed into West Coast GRC.

{{< figure src="/images/sg-electoral-hongkah-2020.png" width="800" alt="Hong Kah Changes" caption="Boundary changes for Hong Kah North in GE2020" class="markdown-image">}}

My armchair speculation:
- Remain as an SMC, with parts being abosrbed into Chua Chu Kang GRC <u>_or_</u>
- Completely absorbed into Chua Chu Kang GRC, and changing the GRC from a 4-member team to a 5-member team

My speculation is based on the fact that Chua Chu Kang could be considered a safe bet given that it is currently anchored by newly designated Deputy Prime Minister Gan Kim Yong. It is unlikely to be absorbed into West Coast GRC, especially considering the close fight in GE2020 where the PAP secured 71,658 votes (51.7%) against PSP's 66.996 votes (48.3%). More on this in the next part.

### West Coast GRC

West Coast GRC is likely to be an interesting GRC in the upcoming GE, given the close contest in GE2020. PAP has also lost its anchor minister in this GRC, following the resignation of former minister Iswaran.

{{< figure src="/images/sg-electoral-westcoast.png" width="800" alt="West Coast Changes" caption="Boundary changes for West Coast GRC in GE2020" class="markdown-image">}}

In GE2020, West Coast GRC expanded with the inclusion of parts from Chua Chu Kang GRC and Jurong GRC. Again, given that Chua Chu Kang GRC could be seen as a safer bet and its proximity to West Coast, there is a high possibility we will see changes there.

My armchair speculation:
- Parts to be absorbed into Chua Chu Kang GRC. West Coast GRC to be reduced to a 4-member team while Chua Chu Kang to be bumped up to a 5-member team <u>_or_</u>
- Parts to be splitted out to form a new SMC together with parts from Chua Chu Kang/Jurong GRC, and reducing West Coast to a 4-member team.

### Pasir Ris-Punggol GRC

Based on the latest figures, Pasir Ris-Punggol GRC saw an increase of 13,629 electors, pushing it to 36,037 electors per MP. In GE2020, it also saw big changes, with parts being absorbed into Tampines GRC and the creation of new Punggol West SMC and Sengkang GRC. 

{{< figure src="/images/sg-electoral-prp.png" width="800" alt="Pasir Ris-Punggol Changes" caption="Boundary changes for Pasir Ris-Punggol GRC in GE2020" class="markdown-image">}}

In GE2020, there was a three-way contest, allowing PAP to secure victory with 100,932 votes (64.2%). 

My armchair speculation:
- Remain as is without any change <u>_or_</u>
- Parts to be absorbed into East Coast GRC, given that East Coast now has a lower number of electors compared to 4-member Sengkang GRC <u>_or_</u>
- Parts to be absorbed into Punggol West SMC (currently at 26,754 electors per MP)

I do not expect parts to be absorbed into Sengkang GRC, which is currently under WP's control. Historically, there have been no changes to electoral boundaries under WP's control, as observed in Hougang and Aljunied over the election years.

{{< figure src="/images/sg-electoral-hougang.png" width="800" alt="Hougang" caption="No boundary changes for Hougang SMC _(note: the red-green boundary lines are merely 'artifacts' due to slightly misalignment in boundary definition across election years)_" class="markdown-image">}}

{{< figure src="/images/sg-electoral-aljunied.png" width="800" alt="Aljunied" caption="No boundary changes for Aljunied GRC _(note: the red-green boundary lines are merely 'artifacts' due to slightly misalignment in boundary definition across election years)_" class="markdown-image">}}

### East Coast GRC

East Coast GRC now has a lower number of electors compared to 4-member Sengkang GRC. One solution would be to bump Sengkang GRC to a 5-pmember team, but this is less likely given that it is under WP's control.

We have seen earlier than Fengshan SMC was absorbed into East Coast GRC in GE2020. Hence, there is a likelihood that this change could be reversed for the upcoming GE. In GE2015, PAP secured Fengshan with 57.5% of vote counts against WP's 42.5%. In GE2020, PAP also faced a tough fight, securing a close 53.4% of votes against WP's 46.6%, although the anchor of WP's team then, Nicole Seah, is no longer with the party.

My armchair speculation:
- Absorbed parts of Pasir Ris-Punggol and remain as a 5-member team <u>_or_</u>
- Carved out Fengshan to be an SMC like in GE2015 and reduce to a 4-member team

### Conclusion

I hope that the dashboard provides a useful tool for examining electoral boundary changes across different general election years. Drwa your own conclusions about whether these changes reflect certain political agenda or constitute gerrymandering. 

As we approach the upcoming general election, the evolving boundaries will be closely watched, and it will be interesting to see how many of my armchair speculations on potential changes prove to be accurate. I will be updating the data once the new electoral boundaries are released. Stay tuned!