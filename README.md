> Step 1. Add the JitPack repository to your build file
> Add it in your root build.gradle at the end of repositories:
```
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```
> Step 2. Add the dependency

```
	dependencies {
	        implementation files("libs/admobnativeteads-1.0.0.aar")
	}
```
```
  implementation files("libs/admobnativeteads-1.0.0.aar")
```

> Step 3


```
  private NativeAd admobNativeAD;
  private AdmobNativeTemplate myTemplate;
```

```
  myTemplate  = view.findViewById(R.id.my_template);
```


```
        AdLoader adLoader = new AdLoader.Builder(context, context.getResources().getString(R.string.Native_Ads_Google_code))
                .forNativeAd(new NativeAd.OnNativeAdLoadedListener() {
                    @Override
                    public void onNativeAdLoaded(NativeAd NativeAd) {
                        // Show the ad.
                        if (admobNativeAD != null) {
                           admobNativeAD.destroy();
                        }
                          admobNativeAD = NativeAd;

                        NativeTemplateStyle styles = new NativeTemplateStyle.Builder()
                                .withCallToActionBackgroundColor
                                        (new ColorDrawable(ContextCompat.getColor(context, R.color.colorAccent)))
                                .build();
                       myTemplate.setStyles(styles);
                      myTemplate.setNativeAd(NativeAd);
                      myTemplate.setVisibility(View.VISIBLE);
                    }
                })
                .withAdListener(new AdListener() {
                    @Override
                    public void onAdFailedToLoad(LoadAdError adError) {
                        // Handle the failure by logging, altering the UI, and so on.
                    }
                })
                .withNativeAdOptions(new NativeAdOptions.Builder()
                        // Methods in the NativeAdOptions.Builder class can be
                        // used here to specify individual options settings.
                        .build())
                .build();
        adLoader.loadAd(new AdRequest.Builder().build());
```
