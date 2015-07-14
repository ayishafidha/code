
% take images from link
     
  clc;
  Image1=imread('http://www.hercampus.com/sites/default/files/2013/02/27/topic-1350661050.jpg','jpg');
  Image2=imread('http://www.kaytee.com/images/anim-small-1.png','png');


%  convert images to type double (range from from 0 to 1 instead of from 0 to 255)

Imaged1 = im2double(Image1);
Imaged2 = im2double(Image2);

% reduce three channel [ RGB ]  to one channel [ grayscale ]

Imageg1 = rgb2gray(Imaged1);
Imageg2 = rgb2gray(Imaged2);

% Calculate the Normalized Histogram of Image 1 and Image 2

hn1 = imhist(Imageg1)./numel(Imageg1);
hn2 = imhist(Imageg2)./numel(Imageg2);
 subplot(2,2,1);subimage(Image1)
 subplot(2,2,2);subimage(Image2)
 subplot(2,2,3);plot(hn1)
 subplot(2,2,4);plot(hn2)

% Calculate the histogram error

f = sum((hn1 - hn2).^2);
disp('difference b/w 2 images =')
disp(f) %display the result to console
