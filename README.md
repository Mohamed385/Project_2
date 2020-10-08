## Which types of events are most harmful to population health?
Fatalities and injuries have the most impact on public health, so I will present what types of severe weather are the most dangerous.
The first plot presents a Death toll by Event type

```
StormData %>%
      select(FATALITIES, EVTYPE) %>%
      group_by(EVTYPE) %>%
      summarise(SumFATALITIES = sum(FATALITIES)) %>%
      top_n(n = 8, wt = SumFATALITIES) %>%
      ggplot(aes(y = SumFATALITIES, x = reorder(x = EVTYPE, X = SumFATALITIES), fill=EVTYPE))+
      geom_bar(stat = "identity", show.legend = FALSE) +
      #geom_text(aes(label=SumFATALITIES), size = 4, hjust = 0.5, vjust = -0.1) +
      xlab(label = "") +
      ylab(label = "Death toll") +
      coord_flip() +
      theme_light()

<img src="Death toll.png">
