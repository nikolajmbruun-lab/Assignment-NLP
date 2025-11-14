Dataset used and subset choice

I used 500 European Parliament debate speeches from 2020 to 2023. I picked this subset because it is large enough to show meaningful patterns but still manageable for running LLM extraction and network analysis without hitting performance limits. The period also captures both stable issues (like climate and EU governance) and major shocks (especially the war in Ukraine in 2022), which makes the networks more interesting to analyse.

LLM extraction process

I used an LLM to turn each speech into structured data. For every speech the model extracted

topics

entities

sentiment

a short summary

The extraction followed a fixed schema so I could later build a knowledge graph from all the triples. I manually checked a sample of outputs to estimate accuracy which I would roughly place at 85 to 90 percent precision and a bit lower recall.

Network construction

From the extracted triples I created several networks:

Speaker–topic bipartite network: links each speaker to the topics they mention.

Speaker–speaker network: projection of the bipartite graph where two speakers are connected if they share topics.

Topic–topic network: projection where two topics are linked if they appear in speeches by the same speaker.

Temporal speaker networks: same construction but split into 2020–2021 and 2022–2023 to compare changes over time.

Party and ideological layer: added left / center / right labels based on party families so I could colour the networks and look at differences across orientations.

Summary of main findings

Across the whole period a stable core of issues dominates: European Union climate change human rights and democracy. In 2022 to 2023 Ukraine rises sharply into this central group. The speaker speaker network is fairly dense and shows that influence and brokerage are shared across several mainstream party families. The topic topic network shows a consistent normative and environmental core plus a clear Ukraine shock in the later period. When splitting the speaker networks by time the later network gets slightly sparser which may point to more issue specialisation.

Limitations

The LLM extraction is not perfect. It sometimes gives very generic topics or misses more specific ones and sentiment is the noisiest dimension. The simplified left center right coding also reduces nuance. The dataset is only 500 speeches so it is not fully representative of the full set of debates. Because of these limitations I treat the results mainly as exploratory patterns rather than strong causal claims.