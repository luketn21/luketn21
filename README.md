#import data
data<-read.csv("/Users/x/Documents/x.csv", header=TRUE)
print(head(data))
#create string for "A" to represent fluorescence
Fluorescence <- data$A
#print
print(Fluorescence)
#create string for "Time" to represent time
Time <- data$Time
#print
print(Time)
#create a function for normalization using formula below
normalize <- function(x) {
  return ((x - min(x)) / (max(x) - min(x)))
}
#"NormFluorescence" now holds normalized fluorescence data
NormFluorescence<-normalize(Fluorescence)
#print
print(Time, NormFluorescence)
#plotting normalized fluorescence data 
df <- data.frame(Column1 = (Time),
                 Column2 = (NormFluorescence))
print (df)

write.csv(data.frame(df),"/Users/X/Documents/Normalized_Chromatography.csv", row.names=FALSE)

plot(Time, NormFluorescence, ylab = 'Delta Fluorescence', xlab = 'Time (Sec)', col= "blue", main = 'Chromatography')

