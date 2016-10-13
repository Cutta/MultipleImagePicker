# MultipleImagePicker for Android
Custom Gallery for Single and Multiple image pick

<a href = "https://android-arsenal.com/details/1/1573"><img src="https://img.shields.io/badge/Android%20Arsenal-MultipleImagePicker-brightgreen.svg?style=flat)](http://android-arsenal.com/details/1/1573"></img>  </a>
Usage
====
This project use Universal Image Loader. Firstly your project must be include <a href = "https://github.com/nostra13/Android-Universal-Image-Loader">Universal Image Loader Lib</a>

After that set your AndroidManifest.xml

<div class="highlight highlight-xml"><pre>
 &lt;<span class="pl-ent">activity</span> <span class="pl-e">android</span><span class="pl-e">:</span><span class="pl-e">name</span>=<span class="pl-s1"><span class="pl-pds">"</span>com.cunoraz.pickImages.CustomGalleryActivity<span class="pl-pds">"</span></span> &gt;
            &lt;<span class="pl-ent">intent-filter</span>&gt;
                &lt;<span class="pl-ent">action</span> <span class="pl-e">android</span><span class="pl-e">:</span><span class="pl-e">name</span>=<span class="pl-s1"><span class="pl-pds">"</span>cunoraz.ACTION_PICK<span class="pl-pds">"</span></span> /&gt;
                &lt;<span class="pl-ent">action</span> <span class="pl-e">android</span><span class="pl-e">:</span><span class="pl-e">name</span>=<span class="pl-s1"><span class="pl-pds">"</span>cunoraz.ACTION_MULTIPLE_PICK<span class="pl-pds">"</span></span> /&gt;

                &lt;<span class="pl-ent">category</span> <span class="pl-e">android</span><span class="pl-e">:</span><span class="pl-e">name</span>=<span class="pl-s1"><span class="pl-pds">"</span>android.intent.category.DEFAULT<span class="pl-pds">"</span></span> /&gt;
            &lt;/<span class="pl-ent">intent-filter</span>&gt;
 &lt;/<span class="pl-ent">activity</span>&gt;</pre></div>
 
	//Calling galery for multiple image
	Intent i = new Intent(Action.ACTION_MULTIPLE_PICK);
	startActivityForResult(i, 100);
				
        //Calling galery for multiple image
	Intent i = new Intent(Action.ACTION_MULTIPLE_PICK);
	startActivityForResult(i, 200);

 Overrie your activity's onActivityResult method like this
 
	@Override
	protected void onActivityResult(int requestCode, int resultCode, Intent data) {
		super.onActivityResult(requestCode, resultCode, data);
        imagePaths = new ArrayList<String>();
		if (requestCode == 100 && resultCode == Activity.RESULT_OK) {
			adapter.clear();

			viewSwitcher.setDisplayedChild(1);
			String single_path = data.getStringExtra("single_path");
            imagePaths.add(single_path);
			imageLoader.displayImage("file://" + single_path, imgSinglePick);

		} else if (requestCode == 200 && resultCode == Activity.RESULT_OK) {
			String[] all_path = data.getStringArrayExtra("all_path");

			ArrayList<CustomGallery> dataT = new ArrayList<CustomGallery>();

			for (String string : all_path) {
				CustomGallery item = new CustomGallery();
				item.sdcardPath = string;
                imagePaths.add(string);
				dataT.add(item);
			}

			viewSwitcher.setDisplayedChild(0);
			adapter.addAll(dataT);
		}
	}
SS
====
 <img src = "http://i.imgur.com/OMkJLDN.jpg"</img>
 

#Credits

<a href = "https://plus.google.com/u/0/116948443141721480957"><img src = "https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/gplus.png"/></a>
<a href = "https://twitter.com/Cuneyt_Carikci"><img src = "https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/twitter.png"/></a>
<a href = "https://www.linkedin.com/in/c%C3%BCneyt-%C3%A7ar%C4%B1k%C3%A7i-b4619161?trk=nav_responsive_tab_profile_pic"><img src = "https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/linkedin.png"/></a>

License
====

Copyright 2015 Cüneyt Çarıkçi

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
