![](https://i.imgur.com/43kusrF.png)

# Art GAN-erator
A project developed over four weeks at the Insight Fellowship that makes use of GANs + Style transfer to lower overhead costs of the ideation process for artists.

## Features
- **Attentional GAN** : Implemented an attentional GAN which is capable of paying attention to the relevant words in a given text input and uses it to generate novel images
- **Neural Style Transfer** : Implemented a fast neural style transfer docker container which takes an input of a content image generated by the AttnGAN and a user given style image and applies the style. 
- **Flask and Docker** : Made use of Flask and Docker to serve the two models in a distributed fashion so that multiple users can use the web application at the same time
- **AWS and PyTorch** : Code on a p2.xlarge AWS machine making use of PyTorch to modify the models as required.

## Setup
Clone repository and run setup.sh in terminal which will install all the necessary files, models and data. This process can take some time as there are around 2GB of files required for this project.

## Usage

# To run the AttGAN model:

cd AttnGAN
python2 gen_art.py --gpu 0 --input_text "the bear is eating a banana" --data_dir data/birds --model_path models/bird_AttnGAN2.pth --textencoder_path DAMSMencoders/bird/text_encoder200.pth --output_dir output

# Move the generated image:
cd output
mv 0_s_0_g2.png /home/ubuntu/neural-style-docker/content.png


# To run the style transfer:
cd neural-style-docker
sudo nvidia-docker run --rm -v /home/ubuntu/neural-style-docker:/images albarji/neural-style --content content.png --style style.png


## Results

