End goal: Remotely locate and track the recovery of past landslides (ideally rainfall triggered)
    
    Intermediate Goals: 
      1) Filter and mask clouds from surface reflectance satelitte images in GEE to get a largely cloud free collection of images
            -  Methods for filtering:
                    - By date (Summer in NZ: Oct. to Jan.)
                    - By region (Aotea)
                    - By CLOUDY_PIXEL_PERCENTAGE (derived property in Sentinel-2 images) with threshold
            - Methods used for masking
                    - By QA Pixels (bitWise cirrus and cloud IDs)
                    - By Cloud Score (similar to UoA Thomas Dowling Lab 2) with overall threshold and score band thresholds
                    - By buffer off of cloud score (mask extension of pixels around where the cloud score was high to block out cirrus cloud edges)
                    - By 'Cloud Probabiliy' (derived band in Sentinel-2 images) with threshold 
      2) Use the now cloud free image collection to produce a composite image for each year (Oct. to Jan. range)
            - Use ideal percentile of the pixel reflectance across the image collection to avoid unusually dark (clud shadow) or light (cirrus clouds) from being shown in the composite
                    - Histogram analysis would be ideal (I have not been able to do this)
                            - See the typical percentile (thresholds) where the regions are generally visible (cloud shadow | clear area (should be around median) | cirrus cloud | cumulus cloud)
            - 'Manual' Mosaic (overlaying images on top of one another to fill gaps)
                    - The number of images after initial filters is manageable to hand sort if needed (typically around 50 for a year)               
      3) Manually map landslides using the visual from the annual composites produced
            - In QGIS
      4) Train SVM and object-based models using the manually mapped landslides
            - Python
      5) Locate and identifty the first occurance of the landslide to allow for recovery to be tracked thereafter
            - Export to Excel
            
Current Progress: Goals 1 and 2 have been completed for Sentinel 2 imagery
    - Next: Configure Sentinel-2 code to do the same for Landsat 89, Landsat 457, and Landsat 123 imagery
