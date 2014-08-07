# Code supplement for Devisetty et al., 2014

## SNP Annotation

Tool:

- [SnpEff](http://snpeff.sourceforge.net) v3.0

SnpEff config file:

- [`snpEff.config`](files/snpEff.config)

Input VCF files:

- `R500_IMB211.2014-03-25.vcf.gz`
- `R500-Chiifu.vcf.gz`
- `IMB211-Chiifu.vcf.gz`

Output SNP/INDEL files:

- `R500_IMB211.2014-03-25.vcf `
- `R500-Chiifu.vcf`
- `IMB211-Chiifu.vcf`

### Annotate R500 vs. IMB211 SNPs

```sh
java -Xmx2g -jar snpEff.jar \
  -no-downstream -no-upstream -c snpEff.config \
  brassica.v_2 R500_IMB211.2014-03-25.vcf.gz \
  > R500_IMB211.vcf 
```

### Annotate R500 vs. Chiifu and IMB211 vs. Chiifu SNPs

```sh
for ID in R500 IMB211; do
    java -Xmx2g -jar snpEff.jar \
      -no-downstream -no-upstream -c snpEff.config \
      brassica.v_2 $ID-Chiifu.vcf.gz \
      > $ID-Chiifu.vcf
done
```
