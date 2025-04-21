# Training

We train our OpenThinker ([7B](https://huggingface.co/open-thoughts/OpenThinker-7B), [32B](https://huggingface.co/open-thoughts/OpenThinker-32B)) and OpenThinker2 ([7B](https://huggingface.co/open-thoughts/OpenThinker2-7B), [32B](https://huggingface.co/open-thoughts/OpenThinker2-32B)) using [LLaMa-Factory](https://github.com/hiyouga/LLaMA-Factory).

We provide our training config files with the relevant hyperparameters:
- [`OpenThinker-7B.yaml`](./OpenThinker-7B.yaml)
- [`OpenThinker-32B.yaml`](./OpenThinker-32B.yaml)
- [`OpenThinker2-7B.yaml`](./OpenThinker2-7B.yaml)
- [`OpenThinker2-32B.yaml`](./OpenThinker2-32B.yaml)

For OpenThinker2, we experimented with a few changes that led to training speedups. These include sample packing, removing CPU offloading, and using persistent dataloaders. We also adjusted learning rate and batch size for OpenThinker2, and we trained for more epochs. More specific details can be found in the [config files](./OpenThinker2-32B.yaml). 

Notably, we use `cutoff_len: 16384`. Some reasoning traces are longer than this. However we found that filtering out traces longer than this did not improve model performance.
