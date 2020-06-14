1. Download Data from https://www.kaggle.com/c/whale-detection-challenge/overview
2. Unzip data into folder named 'data'
3. Preprocessing data by running preprocess.ipynb

In preprocess.ipynb:
  1. Change values of train_spec_dir, test_spec_dir to the one you want:
     ex.
       train_spec_dir = './data/train_prep_10/'
       test_spec_dir = './data/test_prep_10/'
  2. Change the below two conditions to extract part of the dataset.
     ex.
       if( i % _number_ == 0):
       if( cnt % _number_ == 0):

After preprocessing

In the model file:
  1. Change this line to the targeting folder you want:
       image_datasets = {x: datasets.ImageFolder(os.path.join(data_dir, x+"_prep_10_2layers/"), data_transforms[x]) for x in ['train', 'val']}
  2. Change these lines to save the trained model to the correct folder:
       torch.save( model_ft.state_dict(), 'model_weight/googlenet_' + str(num_epochs) )
       state_dict = torch.load( 'model_weight/googlenet_' + str(num_epochs) )
       model.load_state_dict( torch.load( 'model_weight/googlenet_' + str(num_epochs) ) )
       
-Run base models:
  mnasnet1.ipynb
  mobilenetv2.ipynb
  googlenet.ipynb

-Run base models+SVM:
  mnasnet1_SVM.ipynb
  mobilenetv2_SVM.ipynb
  googlenet_SVM.ipynb

-Run small model:
  2_Layers.ipynb
  NN_model.ipynb

-Run Autoencoder model:
  final_NN_model.ipynb
