# Container Signing
# What is Contianer Signing?
Container signing is a way for a user to add a digital fingerprint to a container image. Doing so will allow anyone down the road to cryptographically test the signature agaisnt the public key to verify the trustof the image. The reason this is so important in todays cyber world is heavily due to the shift to secure software supply chains. There has been many significant attacks in recent times targeted towards softwware supply chains, a few bigger name attacks include: SolarWinds, Log4J and Kaseya. These supply chain attacks brought a lot of media coverage and with that media coverage also brought heavy criticism on why we are not securing supply chains properly.

# How To Perform Container Signing
Container signing can be perfomred in a few ways but in this article the one tooling set I'm going to focus on is from the Sigstore Project. Within the Sigstore project there are three applications that when paired together can allow the user to perform container signing with a "keyless" approach. However as of the time of this writing the Sigstore "keyless" approach of signing a contianer image is not yet deemed to be production ready. I will cover more on the "keyless" way of signing later on in this article for now we will focus on the Cosign tool from the Sigstore project. Cosign is one fo the three tools that are provided to you from Sigstore, the use of Cosign on its own can allow you to generate keys to perform the signing. Cosign 1.0 was released in July 2021, deeming the build to be production ready.

# Cosign
Cosign is a fairly straightforward open source tool that anyone can use for performing image signing. At current time Cosign supports the following methods of signing: Hardware and KMS signing, Bring-you-own-PKI, Sigstore's free OIDC (Opend ID Connect) PKI called Fulcio and Sigstore's built in tranparency and timestamping serivce called Rekor. There are four supported ways to perform key management withing Cosign to include; fixed, text-based key generation, cloud-KMS based key generation, keys generated on hardware tokens using the PIV interface and lastly Kubernetes-secret based key generation. Not only are you able to sign and verify an image you can also sign and verify attestations or artifacts within your registry. Getting started with Cosign is super easy and a straight forward install, the [Cosign GitHub](https://github.com/sigstore/cosign) offers a step by step guide for getting up and running in no time.

# Keyless Signing With Sigstore
What is keyless signing?

Keyless signing is a method of signing your images, attestations or artifcats with a short lived ephemeral key. Sigstore's ephemeral keys last for 20 mintues which is enough time for the user to sign anything they desire with said key. These keys are generated and signed by Sigstore's public root-CA called Fulcio. 

As mentioned earlier in the article, if you combine the whole package offering from Sigstore you are able to perform "keyless" signing fo your images, attestaions or artifacts. Keyless signing will offer the end user a simplier and more secure way of performing signatures on anything ebing stored in your registry. This method of signing with lighten the overhead burden of having to manage any sort of key that is being generated to perform the signing, thus making the devoloper and security engineers lifes that much easier. Fulcio and Rekor as briefly mentioned above in this article are two tools from Sigstore that aid Cosign in perfroming this keyless signing approach.

Fulcio is Sigstore's 
