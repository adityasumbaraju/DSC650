---
title: Assignment 1
subtitle: Computer performance, reliability, and scalability calculation
author: Aditya Sumbaraju
---

## 1.2 

#### a. Data Sizes

| Data Item                                  | Size per Item | 
|--------------------------------------------|--------------:|
| 128 character message.                     | 128 Bytes     |
| 1024x768 PNG image                         | 2.25 MB       |
| 1024x768 RAW image                         | 3.75 MB       | 
| HD (1080p) HEVC Video (15 minutes)         | 36 MB         |
| HD (1080p) Uncompressed Video (15 minutes) | 36000 MB      |
| 4K UHD HEVC Video (15 minutes)             | 228 MB        |
| 4k UHD Uncompressed Video (15 minutes)     | 228000 MB     |
| Human Genome (Uncompressed)                | 12.8 GB       |

1. A character is 1 Byte; Hence 128 character message is calculated as 128 Bytes.
2. Step 1 to calculate pixels: 1024*768=786432 pixels.  786432/1000000=0.78 MP
    Step 2: the depth of PNG image is 24 bits and this is calculated as 3 bytes
    Step 3: Calculate  file size: ((786432*3)/1024)/1024=2.25 MB
    Step 4: Aspect ratio: 1024/768=1.33. We can consider compression ratio ~1
    Step 5: Calculate compressed PNG file size: 2.25/1= 2.25 MB 

3. Let's consider the Raw image's depth as 5,Then the size is calculated as 1024 * 768 * 5/1024/1024 = 3.75 MB
4. High Efficiency Video Coding (HEVC or H.265) Video: As per instructions considering Frames per sec: 30 fps and 8 bit depth, 
    video length(vl): 15 miniutes = 15* 60 s= 900 s, 
    HEVC common compression ratio of 1000
    size calculation: 900 sec * 30 fps *1290*1080*8/8/1000/1024/1024, size is approximately 36 MB.
5. Uncompressed Video: the size will be 1000 times HEVC Video, it totals to 36,000 MB.
6. 4K UHD(4096) HEVC Video: the size of 15 mins HEVC video will be: 900s*30 fps*4096*2160*8/8/1000/1024/1024, size is approximately 228 MB.
7. 4k UHD Uncompressed Video: the size will be 1000 * size of 4K UHD(4096) HEVC Video, size is approximately 228,000 MB.
8. Human Genome: Haploid = single copy of a chromosome. Diploid = two versions of haploid. 
    Humans have 22 unique chromosomes x 2 = 44
    A large chromosome take about 300 MB and a small one about 50 MB
    Haploid with large chromosome the size will be calculated as 44*300 MB=13200/1024=12.8 GB

* reference: https://stackoverflow.com/questions/8954571/how-much-storage-would-be-required-to-store-a-human-genome


#### b. Scaling

|                                           | Size     | # HD   | 
|-------------------------------------------|---------:|-------:|
| Daily Twitter Tweets (Uncompressed)       | 59.6 GB  |    1   |
| Daily Twitter Tweets (Snappy Compressed)  | 40 GB    |    1   |
| Daily Instagram Photos                    | 100 TB   |   33   |
| Daily YouTube Videos                      | 99 TB    |   32   |
| Yearly Twitter Tweets (Uncompressed)      | 21.2 TB  |    7   |
| Yearly Twitter Tweets (Snappy Compressed) | 14.25 TB |    4   |
| Yearly Instagram Photos                   | 36500 TB |13272   |
| Yearly YouTube Videos                     | 36135 TB |12045   |

* Instrunctions:
* Twitter statistics estimates 500 million tweets are sent each day. For simplicity, assume each tweet is 128 characters.
1. Daily Twitter Tweets (Uncompressed):Size is calculated as 500000000 tweets* 128 char= 64000000000 bytes; ((64000000000/1024)/1024)/1024=59.6 GB
2. Snappy Compressed: compression ratio is 1.5 to 1.7 times for plain text. hence the size will be approximatly 40GB
resource: https://www.infoq.com/news/2011/04/Snappy/#:~:text=The%20high%20compression%20speed%20is,other%20already%2Dcompressed%20data%E2%80%9D.
3. Daily Instagram Photos: considering 100 million photos per day and size is approximatly 1 MB per photo.size will be 100,000,000 * 1MB=100 TB
resource: https://help.instagram.com/1631821640426723
4. The daily video is 500 hours * 60 * 24 = 720000 hours, 
    In terms of 15 min lengh : 720000 * 4=2880000 . 
    Storage is calculated as
    2880000 * 36 MB = 103680000 MB, = 98.87 TB.
5. Yearly Twitter Tweets (Uncompressed)
6. 59.6 GB * 365 days = 21754 GB= 21.2 TB
7. 40 GB * 365 days = 14600 GB= 14.25 TB
8. 100 TB* 365 days = 36500 TB
9. 99 TB * 365 days = 36135 TB

#### c. Reliability
|                                    | # HD | # Failures |
|------------------------------------|-----:|-----------:|
| Twitter Tweets (Uncompressed)      | 1    |     <1     |
| Twitter Tweets (Snappy Compressed) | 1    |     <1     |
| Instagram Photos                   | 33   |      8     |
| YouTube Videos                     | 32   |      8     |

falure rate is 0.24%
resource: https://www.backblaze.com/b2/hard-drive-test-data.html


#### d. Latency

|                           | One Way Latency      |
|---------------------------|---------------------:|
| Los Angeles to Amsterdam  | 29.79 ms             |
| Low Earth Orbit Satellite | 6.44 ms              |
| Geostationary Satellite   | 120 ms               |
| Earth to the Moon         | 1282 ms              |
| Earth to Mars             | 21.94 minutes        | 

speed of light: 299792458 m/s = 299792 Km/s
distance from Earth to the Moon is 384,400 km
distance between Los angeles to amsterdam = 5,551 mi= 8933 Km
distance between geostationary satellite and earth= 36,000 km
Low Earth Orbit Satellite: 1931 km
distance between Earth to Mars  : 394820363.52 km

one way latency : total distance * speed of light
1. 8933* 1000/299792= 29.79 ms
2. 1931 * 1000/299792=6.44 ms
3. 36000 * 1000/299792 = 120 ms
4. 384400* 1000/299792 = 1282 ms
5. 394820363.52 * 1000/299792 =1,316,980.98 ms = 21.94 min

reference:
https://en.wikipedia.org/wiki/Earth%E2%80%93Moon%E2%80%93Earth_communication
https://www.universetoday.com/38040/speed-of-light-2/
https://www.esa.int/SPECIALS/Eduspace_EN/SEM70Y3Z2OF_0.html#:~:text=The%20geostationary%20orbit%20of%2036%2C000,forms%20of%20telecommunication%2C%20including%20television.

