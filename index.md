---
layout: page
---

<style>
table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  border: 1px solid black;
  padding: 8px;
  text-align: center;
} 

/* Style for the empty cells in the second row */
tr:nth-child(even) td:first-child { 
  border: none; /* Remove border for empty cells */
  padding: 0;   /* Remove padding for empty cells */
}
</style>

# Music2Latent2: Audio Compression with Summary Embeddings and Autoregressive Decoding

__Marco Pasini__<sup>1</sup>, __Stefan Lattner__<sup>2</sup>, __George Fazekas__<sup>1</sup>
1. Queen Mary University of London
2. Sony Computer Science Laboratories Paris


**Abstract**  
Efficiently compressing high-dimensional audio signals into a compact and informative latent space is crucial for various tasks, including generative modeling and music information retrieval (MIR). Existing audio autoencoders, however, often struggle to achieve high compression ratios while preserving audio fidelity and facilitating efficient downstream applications. We introduce Music2Latent2, a novel audio autoencoder that addresses these limitations by leveraging consistency models and a novel approach to representation learning based on unordered latent embeddings, which we call summary embeddings. Unlike conventional methods that encode local audio features into ordered sequences, Music2Latent2 compresses audio signals into sets of summary embeddings, where each embedding can capture distinct global features of the input sample. This enables to achieve higher reconstruction quality at the same compression ratio. To handle arbitrary audio lengths, Music2Latent2 employs an autoregressive consistency model trained on two consecutive audio chunks with causal masking, ensuring coherent reconstruction across segment boundaries. Additionally, we propose a novel two-step decoding procedure that leverages the denoising capabilities of consistency models to further refine the generated audio at no additional cost. Our experiments demonstrate that Music2Latent2 outperforms existing continuous audio autoencoders regarding audio quality and performance on downstream tasks. Music2Latent2 paves the way for new possibilities in audio compression. 


## Architecture
<img src="imgs/music2latent2.png">




## Audio Examples

We compare the reconstructions of Music2Latent2 against baselines for MusicCaps evaluation samples. 
We also include reconstructions from Descript Audio Codec (DAC): altough not directly comparable since it encodes audio into discrete tokens instead of continuous embeddings at a much higher sampling rate, we understand it may be valuable to provide a comparison between the two models.

<table style="margin-left: -5cm !important; width: 150%; border-collapse: collapse; border: 2px solid black; text-align: center;">
  <!-- Sample 1 -->
  <tr>
    <th style="width: 14.28%;">Original</th> <!-- 100% divided by 7 columns -->
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-0SdAVK79lg.mp3" controls></audio>
    </td>
    <td>
      <audio src="music2latent/-0SdAVK79lg.mp3" controls></audio>
    </td>
    <td>
      <audio src="musika/-0SdAVK79lg.mp3" controls></audio>
    </td>
    <td>
      <audio src="latmusic/-0SdAVK79lg.mp3" controls></audio>
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> <!-- 100% divided by 7 columns -->
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td> <!-- Empty cell to maintain structure -->
    <td>
      <audio src="mousaiv2/-0SdAVK79lg.mp3" controls></audio>
    </td>
    <td>
      <audio src="mousaiv3/-0SdAVK79lg.mp3" controls></audio>
    </td>
    <td>
      <audio src="dac/-0SdAVK79lg.mp3" controls></audio>
    </td>
  </tr>

  <!-- Sample 2 -->
  <tr>
    <th style="width: 14.28%;">Original</th>
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-0vPFx-wRRI.mp3" controls></audio>
    </td>
    <td>
      <audio src="music2latent/-0vPFx-wRRI.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-0vPFx-wRRI.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-0vPFx-wRRI.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> <!-- 100% divided by 7 columns -->
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-0vPFx-wRRI.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-0vPFx-wRRI.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-0vPFx-wRRI.mp3" controls></audio>
    </td> 
  </tr>
  
  <!-- Sample 3 -->
  <tr>
    <th style="width: 14.28%;">Original</th>
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-1OlgJWehn8.mp3" controls></audio>
    </td>
    <td>
      <audio src="music2latent/-1OlgJWehn8.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-1OlgJWehn8.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-1OlgJWehn8.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> <!-- 100% divided by 7 columns -->
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-1OlgJWehn8.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-1OlgJWehn8.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-1OlgJWehn8.mp3" controls></audio>
    </td> 
  </tr>
  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-4NLarMj4xU.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-4NLarMj4xU.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-4NLarMj4xU.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-4NLarMj4xU.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-4NLarMj4xU.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-4NLarMj4xU.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-4NLarMj4xU.mp3" controls></audio>
    </td> 
  </tr>

  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-5xOcMJpTUk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-5xOcMJpTUk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-5xOcMJpTUk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-5xOcMJpTUk.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-5xOcMJpTUk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-5xOcMJpTUk.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-5xOcMJpTUk.mp3" controls></audio>
    </td> 
  </tr>

  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-7wUQP6G5EQ.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-7wUQP6G5EQ.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-7wUQP6G5EQ.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-7wUQP6G5EQ.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-7wUQP6G5EQ.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-7wUQP6G5EQ.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-7wUQP6G5EQ.mp3" controls></audio>
    </td> 
  </tr>

  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-8cgbhIR_pw.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-8cgbhIR_pw.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-8cgbhIR_pw.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-8cgbhIR_pw.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-8cgbhIR_pw.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-8cgbhIR_pw.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-8cgbhIR_pw.mp3" controls></audio>
    </td> 
  </tr>

  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-Bu7YaslRW0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-Bu7YaslRW0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-Bu7YaslRW0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-Bu7YaslRW0.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-Bu7YaslRW0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-Bu7YaslRW0.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-Bu7YaslRW0.mp3" controls></audio>
    </td> 
  </tr>

  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-ByoSbgzr4M.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-ByoSbgzr4M.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-ByoSbgzr4M.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-ByoSbgzr4M.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-ByoSbgzr4M.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-ByoSbgzr4M.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-ByoSbgzr4M.mp3" controls></audio>
    </td> 
  </tr>

  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-CUp_Tmg2Y0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-CUp_Tmg2Y0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-CUp_Tmg2Y0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-CUp_Tmg2Y0.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-CUp_Tmg2Y0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-CUp_Tmg2Y0.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-CUp_Tmg2Y0.mp3" controls></audio>
    </td> 
  </tr>
  <!-- ... (continue in the same way for the rest of the samples) ... -->






  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-DeAdhYKbGE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-DeAdhYKbGE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-DeAdhYKbGE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-DeAdhYKbGE.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-DeAdhYKbGE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-DeAdhYKbGE.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-DeAdhYKbGE.mp3" controls></audio>
    </td> 
  </tr>









  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-Dtir74TiUM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-Dtir74TiUM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-Dtir74TiUM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-Dtir74TiUM.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-Dtir74TiUM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-Dtir74TiUM.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-Dtir74TiUM.mp3" controls></audio>
    </td> 
  </tr>









  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-FEPOSP7ay0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-FEPOSP7ay0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-FEPOSP7ay0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-FEPOSP7ay0.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-FEPOSP7ay0.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-FEPOSP7ay0.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-FEPOSP7ay0.mp3" controls></audio>
    </td> 
  </tr>










  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-FFx68qSAuY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-FFx68qSAuY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-FFx68qSAuY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-FFx68qSAuY.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-FFx68qSAuY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-FFx68qSAuY.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-FFx68qSAuY.mp3" controls></audio>
    </td> 
  </tr>










  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-FlvaZQOr2I.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-FlvaZQOr2I.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-FlvaZQOr2I.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-FlvaZQOr2I.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-FlvaZQOr2I.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-FlvaZQOr2I.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-FlvaZQOr2I.mp3" controls></audio>
    </td> 
  </tr>











  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-Gf4Ihv1zwc.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-Gf4Ihv1zwc.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-Gf4Ihv1zwc.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-Gf4Ihv1zwc.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-Gf4Ihv1zwc.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-Gf4Ihv1zwc.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-Gf4Ihv1zwc.mp3" controls></audio>
    </td> 
  </tr>











  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-O9mnfC61Ac.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-O9mnfC61Ac.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-O9mnfC61Ac.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-O9mnfC61Ac.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-O9mnfC61Ac.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-O9mnfC61Ac.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-O9mnfC61Ac.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-OAyRsvFGgc.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-OAyRsvFGgc.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-OAyRsvFGgc.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-OAyRsvFGgc.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-OAyRsvFGgc.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-OAyRsvFGgc.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-OAyRsvFGgc.mp3" controls></audio>
    </td> 
  </tr>













  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-OUIEnuNd1I.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-OUIEnuNd1I.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-OUIEnuNd1I.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-OUIEnuNd1I.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-OUIEnuNd1I.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-OUIEnuNd1I.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-OUIEnuNd1I.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-Q9MTRXS4bE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-Q9MTRXS4bE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-Q9MTRXS4bE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-Q9MTRXS4bE.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-Q9MTRXS4bE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-Q9MTRXS4bE.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-Q9MTRXS4bE.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-QuWdnmn-kM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-QuWdnmn-kM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-QuWdnmn-kM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-QuWdnmn-kM.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-QuWdnmn-kM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-QuWdnmn-kM.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-QuWdnmn-kM.mp3" controls></audio>
    </td> 
  </tr>













  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-R0267o4lLk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-R0267o4lLk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-R0267o4lLk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-R0267o4lLk.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-R0267o4lLk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-R0267o4lLk.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-R0267o4lLk.mp3" controls></audio>
    </td> 
  </tr>













  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-SD43H5B5hE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-SD43H5B5hE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-SD43H5B5hE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-SD43H5B5hE.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-SD43H5B5hE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-SD43H5B5hE.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-SD43H5B5hE.mp3" controls></audio>
    </td> 
  </tr>













  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-W5c6CeUMPE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-W5c6CeUMPE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-W5c6CeUMPE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-W5c6CeUMPE.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-W5c6CeUMPE.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-W5c6CeUMPE.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-W5c6CeUMPE.mp3" controls></audio>
    </td> 
  </tr>













  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-XN0NtrnfMY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-XN0NtrnfMY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-XN0NtrnfMY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-XN0NtrnfMY.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-XN0NtrnfMY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-XN0NtrnfMY.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-XN0NtrnfMY.mp3" controls></audio>
    </td> 
  </tr>














  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-YATTKBtmRA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-YATTKBtmRA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-YATTKBtmRA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-YATTKBtmRA.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-YATTKBtmRA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-YATTKBtmRA.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-YATTKBtmRA.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-_OzT7Xyvok.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-_OzT7Xyvok.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-_OzT7Xyvok.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-_OzT7Xyvok.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-_OzT7Xyvok.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-_OzT7Xyvok.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-_OzT7Xyvok.mp3" controls></audio>
    </td> 
  </tr>














  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-cLzki-B06o.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-cLzki-B06o.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-cLzki-B06o.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-cLzki-B06o.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-cLzki-B06o.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-cLzki-B06o.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-cLzki-B06o.mp3" controls></audio>
    </td> 
  </tr>













  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-eDAoheZrY8.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-eDAoheZrY8.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-eDAoheZrY8.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-eDAoheZrY8.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-eDAoheZrY8.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-eDAoheZrY8.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-eDAoheZrY8.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-f1DNyngKVY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-f1DNyngKVY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-f1DNyngKVY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-f1DNyngKVY.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-f1DNyngKVY.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-f1DNyngKVY.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-f1DNyngKVY.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-i9uQMysy_A.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-i9uQMysy_A.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-i9uQMysy_A.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-i9uQMysy_A.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-i9uQMysy_A.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-i9uQMysy_A.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-i9uQMysy_A.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-jpbCWcz2pk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-jpbCWcz2pk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-jpbCWcz2pk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-jpbCWcz2pk.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-jpbCWcz2pk.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-jpbCWcz2pk.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-jpbCWcz2pk.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-m5ZlWziIeA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-m5ZlWziIeA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-m5ZlWziIeA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-m5ZlWziIeA.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-m5ZlWziIeA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-m5ZlWziIeA.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-m5ZlWziIeA.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-nlkWWphiaM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-nlkWWphiaM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-nlkWWphiaM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-nlkWWphiaM.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-nlkWWphiaM.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-nlkWWphiaM.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-nlkWWphiaM.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-r7iz-9v9bA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-r7iz-9v9bA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-r7iz-9v9bA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-r7iz-9v9bA.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-r7iz-9v9bA.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-r7iz-9v9bA.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-r7iz-9v9bA.mp3" controls></audio>
    </td> 
  </tr>












  <tr>
    <th style="width: 14.28%;">Original</th> 
    <th style="width: 14.28%;">Music2Latent</th>
    <th style="width: 14.28%;">Musika</th>
    <th style="width: 14.28%;">LatMusic</th>
  </tr>
  <tr>
    <td>
      <audio src="real/-tKZOl4q1Kw.mp3" controls></audio> 
    </td>
    <td>
      <audio src="music2latent/-tKZOl4q1Kw.mp3" controls></audio> 
    </td>
    <td>
      <audio src="musika/-tKZOl4q1Kw.mp3" controls></audio> 
    </td>
    <td>
      <audio src="latmusic/-tKZOl4q1Kw.mp3" controls></audio> 
    </td>
  </tr>
  <tr>
    <th style="width: 14.28%; border-bottom: 0px;"></th> 
    <th style="width: 14.28%;">Mousaiv2</th>
    <th style="width: 14.28%;">Mousaiv3</th>
    <th style="width: 14.28%;">DAC</th>
  </tr>
  <tr>
    <td></td>
    <td>
      <audio src="mousaiv2/-tKZOl4q1Kw.mp3" controls></audio> 
    </td>
    <td>
      <audio src="mousaiv3/-tKZOl4q1Kw.mp3" controls></audio> 
    </td>
    <td> 
      <audio src="dac/-tKZOl4q1Kw.mp3" controls></audio>
    </td> 
  </tr>

</table>


<!-- <div class="grid grid-cols-2 md:grid-cols-5 gap-4">
  <div>
    <audio controls>
      <source src="real/-0SdAVK79lg.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-0SdAVK79lg.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-0SdAVK79lg.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-0SdAVK79lg.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-0SdAVK79lg.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-0vPFx-wRRI.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-0vPFx-wRRI.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-0vPFx-wRRI.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-0vPFx-wRRI.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-0vPFx-wRRI.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-1OlgJWehn8.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-1OlgJWehn8.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-1OlgJWehn8.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-1OlgJWehn8.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-1OlgJWehn8.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-4NLarMj4xU.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-4NLarMj4xU.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-4NLarMj4xU.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-4NLarMj4xU.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-4NLarMj4xU.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-5xOcMJpTUk.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-5xOcMJpTUk.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-5xOcMJpTUk.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-5xOcMJpTUk.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-5xOcMJpTUk.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-7wUQP6G5EQ.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-7wUQP6G5EQ.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-7wUQP6G5EQ.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-7wUQP6G5EQ.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-7wUQP6G5EQ.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-8cgbhIR_pw.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-8cgbhIR_pw.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-8cgbhIR_pw.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-8cgbhIR_pw.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-8cgbhIR_pw.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-Bu7YaslRW0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-Bu7YaslRW0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-Bu7YaslRW0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-Bu7YaslRW0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-Bu7YaslRW0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-ByoSbgzr4M.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-ByoSbgzr4M.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-ByoSbgzr4M.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-ByoSbgzr4M.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-ByoSbgzr4M.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-CUp_Tmg2Y0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-CUp_Tmg2Y0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-CUp_Tmg2Y0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-CUp_Tmg2Y0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-CUp_Tmg2Y0.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-DeAdhYKbGE.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Original</p>
  </div>
  <div>
    <audio controls>
      <source src="music2latent/-DeAdhYKbGE.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Music2Latent</p>
  </div>
  <div>
    <audio controls>
      <source src="musika/-DeAdhYKbGE.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Musika</p>
  </div>
  <div>
    <audio controls>
      <source src="latmusic/-DeAdhYKbGE.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>LatMusic</p>
  </div>
  <div>
    <audio controls>
      <source src="mousaiv2/-DeAdhYKbGE.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
    <p>Mousaiv2</p>
  </div>
  <div>
    <audio controls>
      <source src="real/-Dtir74TiUM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-Dtir74TiUM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-Dtir74TiUM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-Dtir74TiUM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-Dtir74TiUM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-FEPOSP7ay0.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-FEPOSP7ay0.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-FEPOSP7ay0.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-FEPOSP7ay0.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-FEPOSP7ay0.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-FFx68qSAuY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-FFx68qSAuY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-FFx68qSAuY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-FFx68qSAuY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-FFx68qSAuY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-FlvaZQOr2I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-FlvaZQOr2I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-FlvaZQOr2I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-FlvaZQOr2I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-FlvaZQOr2I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-Gf4Ihv1zwc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-Gf4Ihv1zwc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-Gf4Ihv1zwc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-Gf4Ihv1zwc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-Gf4Ihv1zwc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-O9mnfC61Ac.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-O9mnfC61Ac.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-O9mnfC61Ac.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-O9mnfC61Ac.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-O9mnfC61Ac.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-OAyRsvFGgc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-OAyRsvFGgc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-OAyRsvFGgc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-OAyRsvFGgc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-OAyRsvFGgc.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-OUIEnuNd1I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-OUIEnuNd1I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-OUIEnuNd1I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-OUIEnuNd1I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-OUIEnuNd1I.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-Q9MTRXS4bE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-Q9MTRXS4bE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-Q9MTRXS4bE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-Q9MTRXS4bE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-Q9MTRXS4bE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-QuWdnmn-kM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-QuWdnmn-kM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-QuWdnmn-kM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-QuWdnmn-kM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-QuWdnmn-kM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-R0267o4lLk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-R0267o4lLk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-R0267o4lLk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-R0267o4lLk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-R0267o4lLk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-SD43H5B5hE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-SD43H5B5hE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-SD43H5B5hE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-SD43H5B5hE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-SD43H5B5hE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-W5c6CeUMPE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-W5c6CeUMPE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-W5c6CeUMPE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-W5c6CeUMPE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-W5c6CeUMPE.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-XN0NtrnfMY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-XN0NtrnfMY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-XN0NtrnfMY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-XN0NtrnfMY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-XN0NtrnfMY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-YATTKBtmRA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-YATTKBtmRA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-YATTKBtmRA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-YATTKBtmRA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-YATTKBtmRA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-_OzT7Xyvok.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-_OzT7Xyvok.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-_OzT7Xyvok.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-_OzT7Xyvok.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-_OzT7Xyvok.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-cLzki-B06o.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-cLzki-B06o.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-cLzki-B06o.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-cLzki-B06o.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-cLzki-B06o.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-cQ-jUTEgck.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-cQ-jUTEgck.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-cQ-jUTEgck.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-cQ-jUTEgck.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-cQ-jUTEgck.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-eDAoheZrY8.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-eDAoheZrY8.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-eDAoheZrY8.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-eDAoheZrY8.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-eDAoheZrY8.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-f1DNyngKVY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-f1DNyngKVY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-f1DNyngKVY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-f1DNyngKVY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-f1DNyngKVY.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-i9gpG3vPwA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-i9gpG3vPwA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-i9gpG3vPwA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-i9gpG3vPwA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-i9gpG3vPwA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-i9uQMysy_A.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-i9uQMysy_A.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-i9uQMysy_A.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-i9uQMysy_A.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-i9uQMysy_A.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-jpbCWcz2pk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-jpbCWcz2pk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-jpbCWcz2pk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-jpbCWcz2pk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-jpbCWcz2pk.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-m5ZlWziIeA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-m5ZlWziIeA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-m5ZlWziIeA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-m5ZlWziIeA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-m5ZlWziIeA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-nlkWWphiaM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-nlkWWphiaM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-nlkWWphiaM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-nlkWWphiaM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-nlkWWphiaM.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-r7iz-9v9bA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-r7iz-9v9bA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-r7iz-9v9bA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-r7iz-9v9bA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-r7iz-9v9bA.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> <div> <audio controls> <source src="real/-tKZOl4q1Kw.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Original</p> </div> <div> <audio controls> <source src="music2latent/-tKZOl4q1Kw.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Music2Latent</p> </div> <div> <audio controls> <source src="musika/-tKZOl4q1Kw.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Musika</p> </div> <div> <audio controls> <source src="latmusic/-tKZOl4q1Kw.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>LatMusic</p> </div> <div> <audio controls> <source src="mousaiv2/-tKZOl4q1Kw.mp3" type="audio/mpeg"> Your browser does not support the audio element. </audio> <p>Mousaiv2</p> </div> </div> -->


<!-- | Original | **Music2Latent** | Musika | LatMusic | Mousaiv2 | Mousaiv3 | | DAC |
|------|-------------------|--------|----------|----------|----------|--|-----|
| <audio src="real/-0SdAVK79lg.mp3" controls></audio> | <audio src="music2latent/-0SdAVK79lg.mp3" controls></audio> | <audio src="musika/-0SdAVK79lg.mp3" controls></audio> | <audio src="latmusic/-0SdAVK79lg.mp3" controls></audio> | <audio src="mousaiv2/-0SdAVK79lg.mp3" controls></audio> | <audio src="mousaiv3/-0SdAVK79lg.mp3" controls></audio> | | <audio src="dac/-0SdAVK79lg.mp3" controls></audio> |
| <audio src="real/-0vPFx-wRRI.mp3" controls></audio> | <audio src="music2latent/-0vPFx-wRRI.mp3" controls></audio> | <audio src="musika/-0vPFx-wRRI.mp3" controls></audio> | <audio src="latmusic/-0vPFx-wRRI.mp3" controls></audio> | <audio src="mousaiv2/-0vPFx-wRRI.mp3" controls></audio> | <audio src="mousaiv3/-0vPFx-wRRI.mp3" controls></audio> | | <audio src="dac/-0vPFx-wRRI.mp3" controls></audio> |
| <audio src="real/-1OlgJWehn8.mp3" controls></audio> | <audio src="music2latent/-1OlgJWehn8.mp3" controls></audio> | <audio src="musika/-1OlgJWehn8.mp3" controls></audio> | <audio src="latmusic/-1OlgJWehn8.mp3" controls></audio> | <audio src="mousaiv2/-1OlgJWehn8.mp3" controls></audio> | <audio src="mousaiv3/-1OlgJWehn8.mp3" controls></audio> | | <audio src="dac/-1OlgJWehn8.mp3" controls></audio> |
| <audio src="real/-4NLarMj4xU.mp3" controls></audio> | <audio src="music2latent/-4NLarMj4xU.mp3" controls></audio> | <audio src="musika/-4NLarMj4xU.mp3" controls></audio> | <audio src="latmusic/-4NLarMj4xU.mp3" controls></audio> | <audio src="mousaiv2/-4NLarMj4xU.mp3" controls></audio> | <audio src="mousaiv3/-4NLarMj4xU.mp3" controls></audio> | | <audio src="dac/-4NLarMj4xU.mp3" controls></audio> |
| <audio src="real/-5xOcMJpTUk.mp3" controls></audio> | <audio src="music2latent/-5xOcMJpTUk.mp3" controls></audio> | <audio src="musika/-5xOcMJpTUk.mp3" controls></audio> | <audio src="latmusic/-5xOcMJpTUk.mp3" controls></audio> | <audio src="mousaiv2/-5xOcMJpTUk.mp3" controls></audio> | <audio src="mousaiv3/-5xOcMJpTUk.mp3" controls></audio> | | <audio src="dac/-5xOcMJpTUk.mp3" controls></audio> |
| <audio src="real/-7wUQP6G5EQ.mp3" controls></audio> | <audio src="music2latent/-7wUQP6G5EQ.mp3" controls></audio> | <audio src="musika/-7wUQP6G5EQ.mp3" controls></audio> | <audio src="latmusic/-7wUQP6G5EQ.mp3" controls></audio> | <audio src="mousaiv2/-7wUQP6G5EQ.mp3" controls></audio> | <audio src="mousaiv3/-7wUQP6G5EQ.mp3" controls></audio> | | <audio src="dac/-7wUQP6G5EQ.mp3" controls></audio> |
| <audio src="real/-8cgbhIR_pw.mp3" controls></audio> | <audio src="music2latent/-8cgbhIR_pw.mp3" controls></audio> | <audio src="musika/-8cgbhIR_pw.mp3" controls></audio> | <audio src="latmusic/-8cgbhIR_pw.mp3" controls></audio> | <audio src="mousaiv2/-8cgbhIR_pw.mp3" controls></audio> | <audio src="mousaiv3/-8cgbhIR_pw.mp3" controls></audio> | | <audio src="dac/-8cgbhIR_pw.mp3" controls></audio> |
| <audio src="real/-Bu7YaslRW0.mp3" controls></audio> | <audio src="music2latent/-Bu7YaslRW0.mp3" controls></audio> | <audio src="musika/-Bu7YaslRW0.mp3" controls></audio> | <audio src="latmusic/-Bu7YaslRW0.mp3" controls></audio> | <audio src="mousaiv2/-Bu7YaslRW0.mp3" controls></audio> | <audio src="mousaiv3/-Bu7YaslRW0.mp3" controls></audio> | | <audio src="dac/-Bu7YaslRW0.mp3" controls></audio> |
| <audio src="real/-ByoSbgzr4M.mp3" controls></audio> | <audio src="music2latent/-ByoSbgzr4M.mp3" controls></audio> | <audio src="musika/-ByoSbgzr4M.mp3" controls></audio> | <audio src="latmusic/-ByoSbgzr4M.mp3" controls></audio> | <audio src="mousaiv2/-ByoSbgzr4M.mp3" controls></audio> | <audio src="mousaiv3/-ByoSbgzr4M.mp3" controls></audio> | | <audio src="dac/-ByoSbgzr4M.mp3" controls></audio> |
| <audio src="real/-CUp_Tmg2Y0.mp3" controls></audio> | <audio src="music2latent/-CUp_Tmg2Y0.mp3" controls></audio> | <audio src="musika/-CUp_Tmg2Y0.mp3" controls></audio> | <audio src="latmusic/-CUp_Tmg2Y0.mp3" controls></audio> | <audio src="mousaiv2/-CUp_Tmg2Y0.mp3" controls></audio> | <audio src="mousaiv3/-CUp_Tmg2Y0.mp3" controls></audio> | | <audio src="dac/-CUp_Tmg2Y0.mp3" controls></audio> |
| <audio src="real/-DeAdhYKbGE.mp3" controls></audio> | <audio src="music2latent/-DeAdhYKbGE.mp3" controls></audio> | <audio src="musika/-DeAdhYKbGE.mp3" controls></audio> | <audio src="latmusic/-DeAdhYKbGE.mp3" controls></audio> | <audio src="mousaiv2/-DeAdhYKbGE.mp3" controls></audio> | <audio src="mousaiv3/-DeAdhYKbGE.mp3" controls></audio> | | <audio src="dac/-DeAdhYKbGE.mp3" controls></audio> |
| <audio src="real/-Dtir74TiUM.mp3" controls></audio> | <audio src="music2latent/-Dtir74TiUM.mp3" controls></audio> | <audio src="musika/-Dtir74TiUM.mp3" controls></audio> | <audio src="latmusic/-Dtir74TiUM.mp3" controls></audio> | <audio src="mousaiv2/-Dtir74TiUM.mp3" controls></audio> | <audio src="mousaiv3/-Dtir74TiUM.mp3" controls></audio> | | <audio src="dac/-Dtir74TiUM.mp3" controls></audio> |
| <audio src="real/-FEPOSP7ay0.mp3" controls></audio> | <audio src="music2latent/-FEPOSP7ay0.mp3" controls></audio> | <audio src="musika/-FEPOSP7ay0.mp3" controls></audio> | <audio src="latmusic/-FEPOSP7ay0.mp3" controls></audio> | <audio src="mousaiv2/-FEPOSP7ay0.mp3" controls></audio> | <audio src="mousaiv3/-FEPOSP7ay0.mp3" controls></audio> | | <audio src="dac/-FEPOSP7ay0.mp3" controls></audio> |
| <audio src="real/-FFx68qSAuY.mp3" controls></audio> | <audio src="music2latent/-FFx68qSAuY.mp3" controls></audio> | <audio src="musika/-FFx68qSAuY.mp3" controls></audio> | <audio src="latmusic/-FFx68qSAuY.mp3" controls></audio> | <audio src="mousaiv2/-FFx68qSAuY.mp3" controls></audio> | <audio src="mousaiv3/-FFx68qSAuY.mp3" controls></audio> | | <audio src="dac/-FFx68qSAuY.mp3" controls></audio> |
| <audio src="real/-FlvaZQOr2I.mp3" controls></audio> | <audio src="music2latent/-FlvaZQOr2I.mp3" controls></audio> | <audio src="musika/-FlvaZQOr2I.mp3" controls></audio> | <audio src="latmusic/-FlvaZQOr2I.mp3" controls></audio> | <audio src="mousaiv2/-FlvaZQOr2I.mp3" controls></audio> | <audio src="mousaiv3/-FlvaZQOr2I.mp3" controls></audio> | | <audio src="dac/-FlvaZQOr2I.mp3" controls></audio> |
| <audio src="real/-Gf4Ihv1zwc.mp3" controls></audio> | <audio src="music2latent/-Gf4Ihv1zwc.mp3" controls></audio> | <audio src="musika/-Gf4Ihv1zwc.mp3" controls></audio> | <audio src="latmusic/-Gf4Ihv1zwc.mp3" controls></audio> | <audio src="mousaiv2/-Gf4Ihv1zwc.mp3" controls></audio> | <audio src="mousaiv3/-Gf4Ihv1zwc.mp3" controls></audio> | | <audio src="dac/-Gf4Ihv1zwc.mp3" controls></audio> |
| <audio src="real/-O9mnfC61Ac.mp3" controls></audio> | <audio src="music2latent/-O9mnfC61Ac.mp3" controls></audio> | <audio src="musika/-O9mnfC61Ac.mp3" controls></audio> | <audio src="latmusic/-O9mnfC61Ac.mp3" controls></audio> | <audio src="mousaiv2/-O9mnfC61Ac.mp3" controls></audio> | <audio src="mousaiv3/-O9mnfC61Ac.mp3" controls></audio> | | <audio src="dac/-O9mnfC61Ac.mp3" controls></audio> |
| <audio src="real/-OAyRsvFGgc.mp3" controls></audio> | <audio src="music2latent/-OAyRsvFGgc.mp3" controls></audio> | <audio src="musika/-OAyRsvFGgc.mp3" controls></audio> | <audio src="latmusic/-OAyRsvFGgc.mp3" controls></audio> | <audio src="mousaiv2/-OAyRsvFGgc.mp3" controls></audio> | <audio src="mousaiv3/-OAyRsvFGgc.mp3" controls></audio> | | <audio src="dac/-OAyRsvFGgc.mp3" controls></audio> |
| <audio src="real/-OUIEnuNd1I.mp3" controls></audio> | <audio src="music2latent/-OUIEnuNd1I.mp3" controls></audio> | <audio src="musika/-OUIEnuNd1I.mp3" controls></audio> | <audio src="latmusic/-OUIEnuNd1I.mp3" controls></audio> | <audio src="mousaiv2/-OUIEnuNd1I.mp3" controls></audio> | <audio src="mousaiv3/-OUIEnuNd1I.mp3" controls></audio> | | <audio src="dac/-OUIEnuNd1I.mp3" controls></audio> |
| <audio src="real/-Q9MTRXS4bE.mp3" controls></audio> | <audio src="music2latent/-Q9MTRXS4bE.mp3" controls></audio> | <audio src="musika/-Q9MTRXS4bE.mp3" controls></audio> | <audio src="latmusic/-Q9MTRXS4bE.mp3" controls></audio> | <audio src="mousaiv2/-Q9MTRXS4bE.mp3" controls></audio> | <audio src="mousaiv3/-Q9MTRXS4bE.mp3" controls></audio> | | <audio src="dac/-Q9MTRXS4bE.mp3" controls></audio> |
| <audio src="real/-QuWdnmn-kM.mp3" controls></audio> | <audio src="music2latent/-QuWdnmn-kM.mp3" controls></audio> | <audio src="musika/-QuWdnmn-kM.mp3" controls></audio> | <audio src="latmusic/-QuWdnmn-kM.mp3" controls></audio> | <audio src="mousaiv2/-QuWdnmn-kM.mp3" controls></audio> | <audio src="mousaiv3/-QuWdnmn-kM.mp3" controls></audio> | | <audio src="dac/-QuWdnmn-kM.mp3" controls></audio> |
| <audio src="real/-R0267o4lLk.mp3" controls></audio> | <audio src="music2latent/-R0267o4lLk.mp3" controls></audio> | <audio src="musika/-R0267o4lLk.mp3" controls></audio> | <audio src="latmusic/-R0267o4lLk.mp3" controls></audio> | <audio src="mousaiv2/-R0267o4lLk.mp3" controls></audio> | <audio src="mousaiv3/-R0267o4lLk.mp3" controls></audio> | | <audio src="dac/-R0267o4lLk.mp3" controls></audio> |
| <audio src="real/-SD43H5B5hE.mp3" controls></audio> | <audio src="music2latent/-SD43H5B5hE.mp3" controls></audio> | <audio src="musika/-SD43H5B5hE.mp3" controls></audio> | <audio src="latmusic/-SD43H5B5hE.mp3" controls></audio> | <audio src="mousaiv2/-SD43H5B5hE.mp3" controls></audio> | <audio src="mousaiv3/-SD43H5B5hE.mp3" controls></audio> | | <audio src="dac/-SD43H5B5hE.mp3" controls></audio> |
| <audio src="real/-W5c6CeUMPE.mp3" controls></audio> | <audio src="music2latent/-W5c6CeUMPE.mp3" controls></audio> | <audio src="musika/-W5c6CeUMPE.mp3" controls></audio> | <audio src="latmusic/-W5c6CeUMPE.mp3" controls></audio> | <audio src="mousaiv2/-W5c6CeUMPE.mp3" controls></audio> | <audio src="mousaiv3/-W5c6CeUMPE.mp3" controls></audio> | | <audio src="dac/-W5c6CeUMPE.mp3" controls></audio> |
| <audio src="real/-XN0NtrnfMY.mp3" controls></audio> | <audio src="music2latent/-XN0NtrnfMY.mp3" controls></audio> | <audio src="musika/-XN0NtrnfMY.mp3" controls></audio> | <audio src="latmusic/-XN0NtrnfMY.mp3" controls></audio> | <audio src="mousaiv2/-XN0NtrnfMY.mp3" controls></audio> | <audio src="mousaiv3/-XN0NtrnfMY.mp3" controls></audio> | | <audio src="dac/-XN0NtrnfMY.mp3" controls></audio> |
| <audio src="real/-YATTKBtmRA.mp3" controls></audio> | <audio src="music2latent/-YATTKBtmRA.mp3" controls></audio> | <audio src="musika/-YATTKBtmRA.mp3" controls></audio> | <audio src="latmusic/-YATTKBtmRA.mp3" controls></audio> | <audio src="mousaiv2/-YATTKBtmRA.mp3" controls></audio> | <audio src="mousaiv3/-YATTKBtmRA.mp3" controls></audio> | | <audio src="dac/-YATTKBtmRA.mp3" controls></audio> |
| <audio src="real/-_OzT7Xyvok.mp3" controls></audio> | <audio src="music2latent/-_OzT7Xyvok.mp3" controls></audio> | <audio src="musika/-_OzT7Xyvok.mp3" controls></audio> | <audio src="latmusic/-_OzT7Xyvok.mp3" controls></audio> | <audio src="mousaiv2/-_OzT7Xyvok.mp3" controls></audio> | <audio src="mousaiv3/-_OzT7Xyvok.mp3" controls></audio> | | <audio src="dac/-_OzT7Xyvok.mp3" controls></audio> |
| <audio src="real/-cLzki-B06o.mp3" controls></audio> | <audio src="music2latent/-cLzki-B06o.mp3" controls></audio> | <audio src="musika/-cLzki-B06o.mp3" controls></audio> | <audio src="latmusic/-cLzki-B06o.mp3" controls></audio> | <audio src="mousaiv2/-cLzki-B06o.mp3" controls></audio> | <audio src="mousaiv3/-cLzki-B06o.mp3" controls></audio> | | <audio src="dac/-cLzki-B06o.mp3" controls></audio> |
| <audio src="real/-cQ-jUTEgck.mp3" controls></audio> | <audio src="music2latent/-cQ-jUTEgck.mp3" controls></audio> | <audio src="musika/-cQ-jUTEgck.mp3" controls></audio> | <audio src="latmusic/-cQ-jUTEgck.mp3" controls></audio> | <audio src="mousaiv2/-cQ-jUTEgck.mp3" controls></audio> | <audio src="mousaiv3/-cQ-jUTEgck.mp3" controls></audio> | | <audio src="dac/-cQ-jUTEgck.mp3" controls></audio> |
| <audio src="real/-eDAoheZrY8.mp3" controls></audio> | <audio src="music2latent/-eDAoheZrY8.mp3" controls></audio> | <audio src="musika/-eDAoheZrY8.mp3" controls></audio> | <audio src="latmusic/-eDAoheZrY8.mp3" controls></audio> | <audio src="mousaiv2/-eDAoheZrY8.mp3" controls></audio> | <audio src="mousaiv3/-eDAoheZrY8.mp3" controls></audio> | | <audio src="dac/-eDAoheZrY8.mp3" controls></audio> |
| <audio src="real/-f1DNyngKVY.mp3" controls></audio> | <audio src="music2latent/-f1DNyngKVY.mp3" controls></audio> | <audio src="musika/-f1DNyngKVY.mp3" controls></audio> | <audio src="latmusic/-f1DNyngKVY.mp3" controls></audio> | <audio src="mousaiv2/-f1DNyngKVY.mp3" controls></audio> | <audio src="mousaiv3/-f1DNyngKVY.mp3" controls></audio> | | <audio src="dac/-f1DNyngKVY.mp3" controls></audio> |
| <audio src="real/-i9gpG3vPwA.mp3" controls></audio> | <audio src="music2latent/-i9gpG3vPwA.mp3" controls></audio> | <audio src="musika/-i9gpG3vPwA.mp3" controls></audio> | <audio src="latmusic/-i9gpG3vPwA.mp3" controls></audio> | <audio src="mousaiv2/-i9gpG3vPwA.mp3" controls></audio> | <audio src="mousaiv3/-i9gpG3vPwA.mp3" controls></audio> | | <audio src="dac/-i9gpG3vPwA.mp3" controls></audio> |
| <audio src="real/-i9uQMysy_A.mp3" controls></audio> | <audio src="music2latent/-i9uQMysy_A.mp3" controls></audio> | <audio src="musika/-i9uQMysy_A.mp3" controls></audio> | <audio src="latmusic/-i9uQMysy_A.mp3" controls></audio> | <audio src="mousaiv2/-i9uQMysy_A.mp3" controls></audio> | <audio src="mousaiv3/-i9uQMysy_A.mp3" controls></audio> | | <audio src="dac/-i9uQMysy_A.mp3" controls></audio> |
| <audio src="real/-jpbCWcz2pk.mp3" controls></audio> | <audio src="music2latent/-jpbCWcz2pk.mp3" controls></audio> | <audio src="musika/-jpbCWcz2pk.mp3" controls></audio> | <audio src="latmusic/-jpbCWcz2pk.mp3" controls></audio> | <audio src="mousaiv2/-jpbCWcz2pk.mp3" controls></audio> | <audio src="mousaiv3/-jpbCWcz2pk.mp3" controls></audio> | | <audio src="dac/-jpbCWcz2pk.mp3" controls></audio> |
| <audio src="real/-m5ZlWziIeA.mp3" controls></audio> | <audio src="music2latent/-m5ZlWziIeA.mp3" controls></audio> | <audio src="musika/-m5ZlWziIeA.mp3" controls></audio> | <audio src="latmusic/-m5ZlWziIeA.mp3" controls></audio> | <audio src="mousaiv2/-m5ZlWziIeA.mp3" controls></audio> | <audio src="mousaiv3/-m5ZlWziIeA.mp3" controls></audio> | | <audio src="dac/-m5ZlWziIeA.mp3" controls></audio> |
| <audio src="real/-nlkWWphiaM.mp3" controls></audio> | <audio src="music2latent/-nlkWWphiaM.mp3" controls></audio> | <audio src="musika/-nlkWWphiaM.mp3" controls></audio> | <audio src="latmusic/-nlkWWphiaM.mp3" controls></audio> | <audio src="mousaiv2/-nlkWWphiaM.mp3" controls></audio> | <audio src="mousaiv3/-nlkWWphiaM.mp3" controls></audio> | | <audio src="dac/-nlkWWphiaM.mp3" controls></audio> |
| <audio src="real/-r7iz-9v9bA.mp3" controls></audio> | <audio src="music2latent/-r7iz-9v9bA.mp3" controls></audio> | <audio src="musika/-r7iz-9v9bA.mp3" controls></audio> | <audio src="latmusic/-r7iz-9v9bA.mp3" controls></audio> | <audio src="mousaiv2/-r7iz-9v9bA.mp3" controls></audio> | <audio src="mousaiv3/-r7iz-9v9bA.mp3" controls></audio> | | <audio src="dac/-r7iz-9v9bA.mp3" controls></audio> |
| <audio src="real/-tKZOl4q1Kw.mp3" controls></audio> | <audio src="music2latent/-tKZOl4q1Kw.mp3" controls></audio> | <audio src="musika/-tKZOl4q1Kw.mp3" controls></audio> | <audio src="latmusic/-tKZOl4q1Kw.mp3" controls></audio> | <audio src="mousaiv2/-tKZOl4q1Kw.mp3" controls></audio> | <audio src="mousaiv3/-tKZOl4q1Kw.mp3" controls></audio> | | <audio src="dac/-tKZOl4q1Kw.mp3" controls></audio> | -->

<!-- We finally present some audio samples of separations produced by the system. By cross-referencing the cluster index with the histogram shown above, it is possible to recognize the class of sources characteristic of each cluster. -->


<!-- ### Example 0

Mix
<audio src="audio/4/mix.wav" controls ></audio>
Cluster 3 (Drums)
<audio src="audio/4/3.wav" controls ></audio>
Cluster 5 (Drums)
<audio src="audio/4/5.wav" controls ></audio>
Cluster 6 (Bass/Toms)
<audio src="audio/4/6.wav" controls ></audio>
Cluster 12 (Crash)
<audio src="audio/4/12.wav" controls ></audio>
Cluster 14 (Vocals)
<audio src="audio/4/14.wav" controls ></audio>

### Example 1

Mix
<audio src="audio/5/mix.wav" controls ></audio>
Cluster 3 (Drums)
<audio src="audio/5/3.wav" controls ></audio>
Cluster 5 (Drums)
<audio src="audio/5/5.wav" controls ></audio>
Cluster 6 (Bass/Toms)
<audio src="audio/5/6.wav" controls ></audio>
Cluster 8 (Guitar)
<audio src="audio/5/8.wav" controls ></audio>

### Example 2

Mix
<audio src="audio/3/mix.wav" controls ></audio>
Cluster 3 (Drums)
<audio src="audio/3/3.wav" controls ></audio>
Cluster 5 (Drums)
<audio src="audio/3/5.wav" controls ></audio>
Cluster 10 (Misc)
<audio src="audio/3/10.wav" controls ></audio>
Cluster 14 (Vocals)
<audio src="audio/3/14.wav" controls ></audio>

### Example 3

Mix
<audio src="audio/6/mix.wav" controls ></audio>
Cluster 3 (Drums)
<audio src="audio/6/3.wav" controls ></audio>
Cluster 5 (Drums)
<audio src="audio/6/5.wav" controls ></audio>
Cluster 6 (Bass/Toms)
<audio src="audio/6/6.wav" controls ></audio>
Cluster 12 (Crash)
<audio src="audio/6/12.wav" controls ></audio>
Cluster 14 (Vocals)
<audio src="audio/6/14.wav" controls ></audio>


### Example 4

Mix
<audio src="audio/0/mix.wav" controls ></audio>
Cluster 6 (Bass/Toms)
<audio src="audio/0/6.wav" controls ></audio>
Cluster 8 (Guitar)
<audio src="audio/0/8.wav" controls ></audio>
Cluster 14 (Vocals)
<audio src="audio/0/14.wav" controls ></audio>

### Example 5

Mix
<audio src="audio/1/mix.wav" controls ></audio>
Cluster 3 (Drums)
<audio src="audio/1/3.wav" controls ></audio>
Cluster 5 (Drums)
<audio src="audio/1/5.wav" controls ></audio>
Cluster 8 (Guitar)
<audio src="audio/1/8.wav" controls ></audio>
Cluster 12 (Crash)
<audio src="audio/1/12.wav" controls ></audio>
Cluster 14 (Vocals)
<audio src="audio/1/14.wav" controls ></audio>




 -->
