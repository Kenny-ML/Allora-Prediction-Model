# Allora-Prediction-Model
Built an AI model for the Allora Forge competition to predict 1-day BTC/USD log returns using the Allora Model Development Kit. Worked with a teammate who sourced resources while I handled the machine learning. Tested across multiple phases using insights from various GitHub repos and documented progress.
I built this model with a clear goal in mind, to predict the next day's BTC/USD log return using a method that holds up in real market conditions. More like a working prediction model that could run in the Allora network.

The work began with me creating a wallet on the Allora Network.
Downloaded the allorad CLI Tool using my Windows Subsystem for Linux (WSL). This was how I went about that, opened my terminal window and ran ```curl -sSL https://raw.githubusercontent.com/allora-network/allora-chain/main/install.sh | bash -s -- v0.8.0``` to install it. After I was done with that, I ran ```allorad keys add <key-name>``` to create a wallet, saving my key name, wallet address and mnemonic.

![Allorad CLI Tool](https://github.com/user-attachments/assets/69cb167f-efbd-41fe-afcb-aac0bd83b8cc)

![For Allora Post](https://github.com/user-attachments/assets/4d32cfe6-96e1-4838-a235-fd4aea077083)

I signed up for the Forge competition on (https://vk4z45e3hne.typeform.com/to/ypA2Yl1J?utm_source=landing-page&typeform-source=forge.allora.network), filled it and submitted it. I got whitelisted not quite easy but went well, but you have to prove yourself to get whitelisted. After successful registration, I downloaded Keplr Wallet Chrome Extension from the Chrome Web Store imported my wallet on it using my mnemonic. Thereafter connected my wallet to the Allora Forge site, but before that requested for some tokens from the community faucet because it gonna be needed.

![Allora Forge Competition](https://github.com/user-attachments/assets/9a5c68a0-3485-48b8-a92b-1c2ec1056afe)

Started building my model using the built out Allora Model Development Kit (MDK) framework from Allora. The models in this framework are optimized for price prediction , but can be otherwise used for other topics. The framework is actually an open source github repository that allows me as a user to spin up an inference model for over 7,000 cryptocurrencies and stocks. The MDK leverages the Tiingo API as a data feed for these cryptocurrencies and stocks, so I got my API key. Guess I spoke too much about the MDK, so let's get back to using it in building the model.

I installed the MDK repository by cloning it in a new terminal window with ```git clone https://github.com/allora-network/allora-mdk.git``` follwed by running this ```cd allora-mdk``` . I created a conda environment with ```conda env create -f environment.yml``` . Installed all required dependencies by running ```pip install -r requirements.txt``` added my Tiingo API key into my .env file running both ```# .env``` and ```TIINGO_API_KEY=your_tiingo_api_key``` together. Took me sometime to get this done.

![requirements](https://github.com/user-attachments/assets/7583fddd-2d1b-4480-8482-6062351fcca1)

Successfully created the model, thereafter trained the model with this command "```make train```". Selected both my data source and my target variable. Forward by selecting my time interval, selected 5min because I'm dealing with smaller epoch lengths necessary to capture rapid changes in the market.

![me](https://github.com/user-attachments/assets/576defe6-61de-4dc3-bbc2-2aeafa5fd2cd)

Move to selecting the start and end dates for my training data, chose mine to be within the range of the past two months. Next was to select the model to train which I chose Regression Time Series from the custom selection. I actually evaluated my model, if you want to evaluate the trained models use this command ```make eval``` . Packaged my trained model into a new folder named allora-worker-forge.

![make eval](https://github.com/user-attachments/assets/34716376-f8ef-4d4d-8e55-ed45ec136d07)

![regress](https://github.com/user-attachments/assets/705dddbe-2db6-400c-87d2-2aa61fdfec93)

![Packaged moel](https://github.com/user-attachments/assets/b5a302f1-05b2-469c-88e1-a04f1976a74d)

All that is left for me is to deploy my worker by exposing the endpoint then finally deploy to Allora Network.

Guess that's all.

gML to every Allora builders.
