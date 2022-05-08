# Timestamped-event
> require(rjson)
载入需要的程辑包：rjson
> require(plyr)
载入需要的程辑包：plyr
Warning message:
程辑包‘plyr’是用R版本4.1.3 来建造的 
> dataPath<-"http://getglue-data.s3.amazonaws.com/getglue_sample.tar.gz"
> theCon<-gzcon(url(dataPath))
> #read 10 line of the data
> n.rows<-10
> theLines<-readLines(theCon,n=n.rows)

#check its structure
str(theLines)
#notice the first element is different than the rest
theLines[1]

#use fromJSON on each element of the vector,except the first one
theRead<-lapply(theLines[-1],fromJSON)

#turn it all into a data.frame
theData<-ldply(theRead,as.data.frame)

#see how we did
View(Data)
