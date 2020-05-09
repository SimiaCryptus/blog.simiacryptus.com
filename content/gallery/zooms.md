{
 "Title": "Infinite Zoom Animation",
 "Slug": "zooms",
 "Keywords": [
 ],
 "Tags": [
 ],
 "Section": "gallery",
 "comments": false,
 "weight": -200,
 "sidebar": "right",
 "toc": false,
 "authorbox": false
}

{{< rawhtml >}}
<p>
    <script src="/js/descent-animator-opt.js" type="text/javascript"></script>
    <div>
    <canvas height="680" id="canvas_1f62" style="display: block;" width="680"></canvas>
      <script>
        var descent = new Descent(800, 800);
        descent.stepZoom = 0.5;
        descent.animate(document.getElementById('canvas_1f62'),
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/d13e9391-36e4-4f58-aed7-d0ae8fb93a4c.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/ecf9217a-4be4-4798-8707-0823a42e9b19.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/948ac098-a52e-4d51-a212-8f565ae76275.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/1139a529-d0fe-4e5b-8a48-59cd1c728b30.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/8b717d08-e175-45f6-a61c-a374b71d4258.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/569f9faa-1445-410f-8422-96b60863dfd4.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/ee83fca0-67e8-4beb-8528-5e7a5be6ffa5.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/789189ae-ced5-41b2-8822-eb07f5e3c887.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/f8581b7f-b4c4-42de-9dd3-44e4fa043c3e.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/b9b98d27-cf52-4682-b8c4-b08415073722.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/4bbfb7e2-3b09-4afc-80c1-09f163d8efe7.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/cc1935bb-9475-46c7-a8ce-a46850308a37.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/e34ebf54-912c-4440-9ab2-720579aadac1.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/542ea126-0964-4e34-90e0-fb3b145d560c.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/43040c59-5a84-4329-8b98-07bf56c7461b.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/87b50bd0-a318-449d-b61a-80b20d6a82e8.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/6ca7c5d1-0891-47be-8c42-58d982a0c5b6.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/c2bae4e0-96a9-4a1b-b557-0d4d06a4f3b3.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/58aaecb1-2b66-4413-bc7a-915db25b0d0c.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/b5e0ec8b-8177-496f-b9dc-21d34e861464.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/825c74ed-d475-4f46-bada-2561146207d6.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/67e75c25-8913-4a53-b2d6-e18b2dbe9b87.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/88bb321c-f854-408d-9feb-e4ea45e45b84.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/d154bae0-247f-4178-ade2-30841c267c28.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/8a77425f-787d-4656-b018-5341284386a8.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/f3351e3c-8c6c-4430-8560-58d4fd282ede.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/fd67437c-6658-449d-8a7e-70b6b16fe18c.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/f7958ff6-4437-4e8c-a561-4e69fd16b583.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/93eeceae-8229-4e06-a982-9406429448eb.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/226d58f5-f7fe-4034-b8d0-2c2ff5742f39.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/041baa4b-06d6-4000-aad5-23eacf96be30.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/71bf8e95-36fe-426b-a46b-5d9aa9730cd9.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/38d1bf7e-a805-4ed3-8ad0-b74f894ce1d0.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/921542d7-7c7c-40ff-a07e-99c935e5fd44.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/f1228099-30d0-4079-851c-5b9966250254.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/06948c5d-d93a-498f-8de3-fd0a74b9cc46.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/9df5e314-2863-44e6-882f-08b04bcf2d51.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/e54b1c68-6ca8-405a-b384-2dd07e3debe7.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/856d926e-2470-4a3e-8e28-410c791c1e3b.jpg');
    </script>
    </div>    
</p>
{{< /rawhtml >}}

<!--more-->

# 1

This animation cycles through keyframes inspired by sample paintings. 5-part rotational symmetry is preserved through the painting process.

{{< rawhtml >}}
<a href="http://examples.deepartist.org/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/ZoomingRotorEC2$.html"><div>
    <canvas style="display: block" id="canvas" width="800" height="840">
    <script>
        new Descent(800, 840).animate(document.getElementById('canvas'),
            'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/e8854e2d-8713-4423-910e-dc386f781126.jpg',
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/66a1a702-f743-4392-8e50-cd407722b5b9.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/702579b2-b156-413e-b4cc-b1e1152f50ae.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/e8f82f92-4109-43c0-ad5b-34310bf9a0e9.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/9b2920fb-baba-41b3-971f-21189725dac4.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/3f313cd8-15b8-4fce-a068-e76a0ec7a585.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/b513422f-dc71-462e-8562-1943708df71c.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/a006d8c3-9f59-4ae8-9283-7d98c886f24d.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/b9907753-8c8e-4116-94df-db7d5ae2888f.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/7d1632a7-4aa0-43cb-89df-0fd5baec860d.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/4eee13e3-f331-4e1f-a0d1-8870fd2151c2.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/960c02a3-783a-4f30-bcea-88ea17ba65a1.jpg",
            "http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/694bab74-52c7-4df2-afb8-0f50b714ca41/etc/4fe83a2d-ce2c-4f1b-a4cd-c614190ec1df.jpg"
        );
    </script>
</div>
</a>
{{< /rawhtml >}}

# 4

This animation cycles through some chosen input images to produce a stylized zooming sequence animation.

{{< rawhtml >}}
<a href="http://examples.deepartist.org/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/ZoomingRotorEC2$.html">
<div>
      <canvas style="display: block" id="canvas_9fd" width="640" height="640"></canvas>
      <script>
        var descent = new Descent(640, 640);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_9fd'),
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/f62b1844-b71e-4245-9531-1daed3ce8f3b.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/e54edb39-ddc1-40df-9ff4-4d81b1289dcd.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/825532ea-4064-48d4-9ace-4a400cfcb869.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/82962ff2-1627-4906-8257-3b411f46a5ec.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/8c843a21-29b1-4c61-adea-773499642638.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/ed310309-72c1-4a9c-a7f4-0233d2386994.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/f2f2c5e1-2987-4706-89eb-f0826e960e80.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/217b6f19-3b0e-45be-9e52-8242ed358bab.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/93827313-174e-4990-97c7-98389ffb8869.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/ec200fb4-fe48-4c1c-9d43-797f042250f2.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/8d319f5d-8b65-4269-b68c-cb425744c415.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/e1245a24-ffc0-4b8b-960f-50996c323181.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/5e006683-412a-401b-a603-b89b38ccfd96.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/b8e96b33-2117-4d2c-8230-379f7f9d591e.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/de474273-0c3c-447a-8ed6-3d228e2bd63f.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/3f7933e8-b7dd-43ba-9371-7c0d56f6b133.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/df3ec340-f4c2-44fd-8399-4f8bf843d7e8.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/1a44cb86-b208-4d4c-864c-a8c10e83fe95.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/b40e6b1a-1746-4694-9de7-1a9297840816.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/2987dce5-88ce-4b51-8272-f62edb719237.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/7a4ed30e-afc2-45be-9a55-faa96a88a308.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/bc167da7-fe87-4958-bdee-9d48158df8ef.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/fd90954d-c81a-4d06-b823-371ac3fb32e3.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/41d84ada-c60d-4939-ad95-b30488399a12.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/b662dc26-3f15-457b-a3b1-f81196f467df.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/cc7b5567-a963-4394-852e-b5f42a9545f0.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/da1513ba-c6d3-4fca-94da-21f9cd906c6d.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/6c602bff-910b-4c50-b213-16a3b45f6164.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/c464ba0a-7847-4d41-a4e0-43799dadef3a.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/10d879b7-7d53-46ba-83ba-37e3839222e1.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/3520167d-c151-446d-abef-757a9845b0ea.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/2af9e4e2-d0f1-4b96-8dcf-324c22a5d549.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/e20e7f3a-3f21-4279-abb2-716b4062ba73.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/1cd5aa9d-28a1-452c-9ae1-b53a8411f18f.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/c01c183a-b5d1-4b40-b6ac-fcc59b459770.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/052e647f-60c1-4058-beba-c06bd42bd8e0.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/3c657ea3-abad-4005-a70a-0aa6fcc064e4.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/4f8373c1-970d-4c38-8d90-1c117ad75797.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/46cde2ef-f08b-45c3-8374-7ff720eab986.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/13d4346d-7c61-4438-9a00-83c2dc8fcc5d.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/482c6950-c3d1-45ae-a4e6-8e1897b939bb.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/13a23123-fedd-47f0-a4b2-88362e9c2240.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/58c74bbf-23d0-4342-b0ac-cc7e11dfc03d.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/38c97db5-8605-4575-9356-ddaa2980e615.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/7c943432-ee10-47ff-98c2-531a4fc06d8c.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/36082a41-bc16-4e44-8a1d-6490166824fe.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/d103e8fd-47e2-4195-8858-13f5d7f07cb7.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/8e937d46-4286-48fd-9d82-ad0a19546cb6.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/b5dad3a7-c9a5-4a73-9af0-bd2a27d1779d.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/708316b2-3244-43ed-a973-7d77a26926ae.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/3abdf13d-20ba-4d84-8306-3a281886ce32.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/45a01a48-eba6-4b21-9650-21f111f0eab6.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/d0ddd62a-a319-4b73-8295-ac601804dc55.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/38e0b0d4-5334-4be5-8b10-ab6536448e08.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/55c30956-419a-4b57-9c2b-d2ae1cf0cec6.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/bc94d8ac-d6bc-4918-809a-25c286c4920e.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/363a770b-3d4a-4397-8073-69b0991c6788.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/3abf5fe8-4465-49e8-8d98-5d2e07ccb2e9.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/d5e35103-9d8e-4e82-ae81-e066056dd1b8.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/fa092fa6-8255-406c-8bf4-4c3ec450a1de.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/64955599-2950-46d1-8a2c-4974dc68b3f4.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/b637a3ec-129d-4668-a69f-a4341849bb91.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/861edb17-4d2b-4e0c-a882-456d87e3fc65.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/cbb30fbe-c53a-47c2-b885-887e856f4b8a.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/cc73948b-b7ab-4958-a13b-ead1961626a4/etc/5f940c54-e344-4271-88b2-15bb7cd0244f.jpg'
		);
      </script>
    </div>
</a>
{{< /rawhtml >}}

# 2
A zooming animation sequence using keyframes inspired by pictures of flowers.

{{< rawhtml >}}
</a><a href="http://examples.deepartist.org/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/ZoomingRotorEC2$.html">
<div>
      <canvas style="display: block" id="canvas_c7" width="640" height="368"></canvas>
      <script>
        var descent = new Descent(640, 368);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_c7'),
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/4fdba51e-48fe-4d3f-a41c-9b5401fce8a0.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/67b25b63-1b01-4113-8800-9cff20781313.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/db8fd3a1-f07b-4c5f-8866-77fc934db2f6.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/8cf9ced6-c55f-479d-8d56-82f5e02ed19e.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/6661b550-0db0-4e85-a953-41ba9c4e3708.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/b480649e-8eee-41e5-91e8-97a7393f33d4.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/11025746-ea59-4f7e-9335-f10312adc2d8.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/e5daf6e9-99bd-4680-9603-f191a6cea7f7.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/aa995d17-2ae2-4922-9363-fe078e6edfd9.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/80222e97-4e71-4db6-8f63-a01bc37a76db.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/8a6194ea-133d-4c26-910a-ec0e273da1d1.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/0b08a9df-b9b3-4e62-b170-5f81999dbb50.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/21a2d2d0-abb4-452f-8934-1f6c57be11d8.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/b9c7378c-d052-4fbe-940f-b7909c0cfefc.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/f76dd96f-15d6-4ea8-bb98-e7c29b833b97.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/4c7e927b-8501-41d8-a3cc-dc3bb7bc1c30.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/d4404a87-57ac-4f4d-b362-b404c1d050a4.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/733dd751-cdcb-4940-a15e-0dd3ac78aad8.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/64b5045a-2557-4fd6-b300-3e5f0f671c8d.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/f2f16ba5-b916-4fa0-84a7-a14a6aeb23dd.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/2603ba80-02b3-4160-807d-802f1b69a3a6.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/83a46e5c-87f0-4bc5-808b-165d6df37912.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/15d04d9d-84a8-4f17-9415-149aca2783a6.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/81662fe6-6009-4d8e-bd27-5966ce0fd38c.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/447a4e2e-821b-4b78-8bf7-eb1f7b416e80.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/9ae8dd53-8cd7-4e51-a79e-2cefa20ff401.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/08cb0289-64fc-410f-8837-adf67c6686e5.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/bf3caaf4-b138-42ff-b757-8cd1cda43409.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/edd0936e-e3a6-4df7-91c9-0be8a96eb51b.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/84704db7-3eb9-49bf-804d-2d72e1a3a43b/etc/c4084c11-517d-4fc0-bef7-6ff95c52a00f.jpg'
		);
      </script>
</div>
</a>
{{< /rawhtml >}}

# 3

An animation demonstrating a higher enhancement coefficient, using a single keyframe inspired by water.

{{< rawhtml >}}
<a href="http://examples.deepartist.org/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/ZoomingRotorEC2$.html">
<div>
      <canvas style="display: block" id="canvas_2197" width="800" height="800"></canvas>
      <script>
        var descent = new Descent(800, 800);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_2197'),
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/a5a61c69-82af-415c-a63a-330c8371916a.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/d86cb003-512d-4096-9449-40182d617864.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/e2a4bc08-93d1-4930-8894-e176a0d49b14.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/98d7f1bf-c357-4461-818c-178354ccc0b3.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/dd9b22bc-b79e-4af7-b0b3-d0f31df2b0aa.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/f58e9ecd-158e-4b40-a1db-f2f10198d4ec.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/030d9846-3496-48b0-9a68-f376aa519af7.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/a72de61d-50f3-45a9-9e4b-6b2b083f5bca.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/09817f53-9f71-4d2b-9350-ea1e1a9040af.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/fa98b1d3-51f9-42e8-9560-7b5a249caaad.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/b0cd4548-212f-4a10-8c6e-6d6f64867f42.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/eb636bcb-98a7-4dbf-b460-e8a4d5599d65.jpg',
			'http://examples.deepartist.org.s3.amazonaws.com/ZoomingRotor/bcbfe831-0065-4e21-92a9-ba0e7ec3f87f/etc/10923bea-cf2a-462c-a85f-207b02848136.jpg'
		);
      </script>
</div>
</a>
{{< /rawhtml >}}
	
# 6

This is a good example of color-cycling symmetry. Notice the blue, red, and green counter-elements and resulting 6- and 3- way symmetry.

{{< rawhtml >}}
<a href="http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/AutoZoomingRotor.html">
<div>
      <canvas style="display: block" id="canvas_949" width="1024" height="1024"></canvas>
      <script>
        var descent = new Descent(1024, 1024);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_949'),
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/d09643ad-070e-4e66-95c9-1328c942f251.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/f89475ce-d456-4558-b9a9-08d7af981743.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/ae1df11c-b3cc-4f9c-bf97-b0f0c8a1a690.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/58465a20-d5ac-47ff-9cba-e578428aa62a.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/7e56f6a1-2802-4303-acdf-9f260bb0e750.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/c22dd394-9487-4f41-a05b-f9e20ccc8334.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/be068057-92d9-4d35-8390-876a0c196e16.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/595f992d-5bee-4219-89a3-ce598b0e9ef3.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/91cd3e26-8b65-4cca-b9b6-5a5733f680bf.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/f596644f-c2c5-4962-8780-58de5c10592e.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/0fd86d9d-62f8-486b-9021-c1fe89a60073.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/4f920768-a3b8-49bc-bb8c-58fdb702b83b.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/d5ddb226-11ed-4ec0-ad21-b5e5e82105da.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/f046ec81-e1c9-4c2c-a31b-7d5ace8250f4.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/e4522739-371d-48bc-afdc-31ef199105c6.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/92437261-a9bd-4e16-92af-a69eec020a35.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/b92a8791-21b6-4e28-9691-a49edd1684bc.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/131621ad-315b-4f76-a7c3-75d41428e288.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/6722ad0d-f3f2-4afd-94ec-dbe06ae22faf.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/bbd50b8f-01fd-4e07-a6ab-4853299ec7ea.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/bbc8f593-b017-4b99-8953-a52cbb0c0271.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/106f304f-93aa-4793-b043-8023f640c412.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/71d3b47c-3949-4d71-98ac-7581d948f562.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/f0318e67-090b-4834-b44a-f98abefe3545.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/01f17cc3-f3f5-4286-b316-fa4c634ee9d9.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/17dd7eaf-0af7-4e0b-b0a5-405d2cff865f.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/54be88a8-612a-4236-9d8f-0eea525eeabe.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/a75fad63-4e0c-4378-8ea8-64f141c823d2.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/adb73a4e-c1ad-47d4-89f3-0d2bf3cbc56a.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/da95c9b6-8cc9-4c3f-821f-5ba59142fbaa.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/befa37ef-6013-4198-9536-92023dd49948.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/9a736606-bb56-412e-83a8-acc88007756c.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/4981a7f8-a5f3-4a73-948d-16dc40307a66.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/7f06e768-605a-4030-84a3-96e8830308f6.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/fb370057-4185-4c31-a871-de3b914b02a5.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/1c2b44cb-ecbd-42e1-a01c-a3360106877e.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/3c31b414-0701-4767-8da2-997cf36ab463.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/1d9b6d74-599e-42b7-b358-5d83df109d79.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/fb261bcc-4f11-4a06-8613-d06e3bea1635/etc/bde34b64-c86d-482c-a27c-02c0b6c63fc6.jpg');
      </script>
    </div>
</a>
{{< /rawhtml >}}
	
# 5

{{< rawhtml >}}
<a href="http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/ZoomingRotor.html">
<div>
      <canvas style="display: block" id="canvas_1971" width="800" height="800"></canvas>
      <script>
        var descent = new Descent(800, 800);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_1971'),
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/deb36f7f-e707-46fd-b954-e87dfc56c4f9.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/37e7e720-4b5f-45d6-b876-0662234a6a98.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/d54765df-d344-4969-a047-c0151588711c.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/e62046d1-07fb-4bb2-9939-a217dc1c8c32.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/00df761c-b185-4ab8-9cd5-d21d94aaf089.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/97ffdfbf-5cd6-42a7-94eb-d71e5d636acf.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/11d62359-703a-4fa4-8c80-ce720d069c98.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/51a2f8cd-2f01-4ab4-95ba-1c6d283fc8b3.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/96808c38-ef13-470a-bf51-524c9d666cde.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/c1be1f48-8ba9-4013-9604-0a0ab4f73ff7.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/a9f1f4d0-d945-48f1-89bd-4dfec9148402.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/14bb682e-ad3f-449e-91bb-7cc50a4b0cff.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/8eb821a7-c553-4fab-80df-a08fad3b0eb6.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/d650eb5b-4cd4-4497-b3b0-e4c6f9923a48.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/d32047c3-f767-42a4-b5e1-e528ce62f639.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/5e3674e6-bb86-466e-9b5a-8b6ff7183447.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/46ca13b4-b655-4d09-b1dc-8f69696a41ff.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/2dc24a91-02c4-42c0-8956-e091eb5e5e1e.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/a5d00033-49bf-4dab-9f71-875f64940eba.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/969c4fce-3cbb-4266-b83b-eadcd4f4e753.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/99833488-8b41-4b50-8ea7-3806ce428c21.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/f3f44866-a2d3-451b-a95a-7dac98e6a05a.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/a555a4fa-8bd4-40bc-905d-bc3ab3273ab6.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/cf12112f-271b-4e03-993a-bdff9acf2316.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/a849850c-330b-4d63-ad1b-207b3f5ff5cd.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/3eeaba28-b9bb-456f-a82a-a4aa6f46b471.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/125dfde7-3605-4c46-b97a-2716abc03dcd.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/647835d7-1494-4674-bdb9-80639c73f392.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/2a23244d-0c0d-4efc-b4a1-e507ce3594ff.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/c739f1ad-9432-4fb8-9390-f1a5666ab657.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/ab6fc637-796e-41f6-95fa-acc6c383bdfd.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/d43c61fc-c1c5-45c1-be87-047b967575f6.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/4a4fc251-0cc5-4890-b586-e5ce8cbcd234.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/46c4b2d4-7503-4fec-90ac-8c0e271bd92f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/1e9ff08a-fffb-4694-b5c0-7c5455208416.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/6782d278-4e63-4fe0-ab0f-36bea023ecf9.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/8c42bd15-3db5-4ed1-96d5-ab0be445fb63.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/0545d16c-7442-4e5f-b474-d4238a6f35f8.jpg',
			'http://examples.deepartist.org/ZoomingRotor/4ba2357a-9dcb-4990-8ccb-cb01ddf2d4cf/etc/9f4532ee-5ba5-4777-ba69-da72af6e222a.jpg');
      </script>
    </div>
</a>
{{< /rawhtml >}}

# 7

{{< rawhtml >}}
<a href="http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/ZoomingRotor.html">
<div>
      <canvas style="display: block" id="canvas_fcf" width="800" height="800"></canvas>
      <script>
        var descent = new Descent(800, 800);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_fcf'),
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/eed537e8-dc94-467b-84f8-9d76f774cc41.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/f027e52d-663c-4e9d-ae00-a528232c4245.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/a9a32049-1cec-4a69-a874-698da5c647e2.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/76232c33-fe94-4920-a46f-30354b98c1bf.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/70b173ae-5c9d-45a2-9440-b517d56489cd.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/f0fe26cf-5ada-4550-bbfb-0a4a9ffad847.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/c3c35895-dedf-4adb-9ef9-6a65c5c0f455.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/147d9269-624d-4fb5-ad66-f720f0dedc3e.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/c7446dfa-1036-42d3-a559-b08242a5ce90.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/f850f413-f62c-4044-b7e8-5508152b14a5.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/20ca20d3-ec0d-421d-b05b-2ba6f48ce538.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/cc758a96-ffaa-4fa2-828a-ca0c9d1b3f39.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/45cba24a-9be6-4f86-a3e0-0c8b8e545a61.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/f56b56a5-3b45-4fe7-9286-22ae7b64008b.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/45b9152a-e610-4683-b9b0-5e6b9ea68218.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/5fdc456f-402c-4523-b1aa-5d879d2b2d9d.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/cd800f8e-7718-4253-b416-9cb4a24a51a3.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/5bd7c466-3559-429d-9097-e6f50cd27954.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/27eb3185-cb31-40cc-bb1e-1f4928f2adaa.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/3094eee1-455f-4c75-9e33-a29e6980cda3.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/4400a421-ac5d-4b43-b025-faecc9188604.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/4b652b86-08d4-40b5-afa6-5bfe8c62db78.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/b3aebddc-d63c-49e3-8bfe-692c3ad1e947.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/a7b0cd9b-664f-40a8-9a41-0fa8f8bb1b2d.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/c9a615b9-654e-498a-b49b-a10380a4888f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/feab0e18-df11-4c30-8574-a65042465f88.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/2f2a4498-283c-46aa-94b7-824d8b597fa8.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/fd21e577-97e2-4357-a693-5daa5a1c7203.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/6a2f6e54-cd7a-4c45-b750-764625144dd7.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/d0d31b20-ba65-4e47-b535-fecf2b1449fb.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/488e412a-6f77-44f3-9a2c-1d7edc58e391.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/e15b2bab-c51f-46f6-8509-fd47d4218562.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/a2990e0b-b8e7-43ac-b875-6c73c9aa6ffa.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/c49313a5-0a37-4630-9465-6840782cc524.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/5a5bacaf-82cb-441b-a64d-847a5c017c0a.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/eca9ee19-ff7d-4539-a5db-943ab42a30a2.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/979d6f50-d316-40f0-bd29-9d0d1e04d924.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/c9b306e5-17dd-4294-8e7e-a112adff8054.jpg',
			'http://examples.deepartist.org/ZoomingRotor/d80942e1-ad04-4430-99b6-3477d67cb841/etc/a741783c-5dd1-4bb2-bf15-d95a19de5896.jpg');
      </script>
    </div>
</a>
{{< /rawhtml >}}

	
# 8 

{{< rawhtml >}}
<a href="http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/53782ee07fb842859239a54c6aec7258.html">
<div>
      <canvas style="display: block" id="canvas_1863" width="800" height="800"></canvas>
      <script>
        var descent = new Descent(800, 800);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_1863'),
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/112f2800-0c1c-4106-8323-0ba17d8f694e.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/1d789909-ec75-4dc6-bf88-293bee8bfe28.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/49460f09-6333-4a41-a954-6f1931fe05cb.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/88fa004b-896a-4afe-8611-6fd8e0c8f894.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/eae905b7-47a2-461f-8cc3-18f7f453235f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/5c698e6b-a0ba-4119-831f-374840c47862.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/50d360df-1706-4b3c-8c00-489075fd3e73.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/80640077-a5e3-48b5-969c-f6d2c3588d0d.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/dd106c53-d983-4a45-b44a-0750309311d8.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/f047360d-f85c-4e4b-b2a7-417eaa32042c.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/b736f913-cfa2-4974-8fe6-6e5d286ff7fc.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/4ca5c4cd-afa1-406a-941a-a7e6e70161f6.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/c3631a81-8ddf-42de-b727-1fa1d9643360.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/cd7b65ed-c6f1-4b64-a44f-ee90dc816bf2.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/0aca4720-ac54-419e-bc31-9f35edbf187a.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/ff230746-8c6c-48fc-a4a6-6a73868f38ed.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/d6ece707-f8f7-4cf1-8b92-3f434de4f83b.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/6ca1b08e-074e-421c-ac45-0325c9b3c259.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/a046c338-cce0-4ad2-b607-df1aee2df7e6.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/9bf9181e-ae94-4b92-8448-c31f9237a963.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/4a521961-d761-4594-9269-f80e768438d6.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/041cb832-91d4-4401-a6df-2a230127c6b3.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/e50a018e-9f1e-4c33-b9c3-6bcfb5729e48.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/4c63a5d8-47ab-458a-bc02-042017388545.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/98004b3e-db6a-4e60-92cf-ed61a863e867.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/cbb18b1b-403c-4d92-9501-6000e0e404de.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/44ae63dd-8590-4981-9645-098f053d8165.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/6dc678e2-54ce-406c-a9d8-f978664f5116.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/8898acf3-306d-4fec-aa30-7bf1869612c3.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/c5f21da9-ea58-40e5-a94d-94e197d2a386.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/ae3bb07b-6c46-4104-af31-bde5ab5288c2.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/b4731308-0adb-491b-a4f9-00d933d00de3.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/6606726a-aac6-42b5-ae72-13e85a1da853.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/5ae0b4ee-393d-4a3d-ae20-1ffc588b9002.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/0f904023-5a22-49e0-9643-1254704744fd.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/06ef2284-161c-4444-afb4-44bb9de1aaa8.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/a711203e-6b3d-4abe-af68-09abe80ecc12.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/8dc72f26-3968-4ab3-8c23-844f5db7767e.jpg',
			'http://examples.deepartist.org/ZoomingRotor/7ad4dae2-1976-41d5-9eff-2827f1847f2f/etc/530b18f7-f996-4b69-9e63-3ea5155d4370.jpg');
      </script>
    </div>
</a>
{{< /rawhtml >}}
	
# 9

{{< rawhtml >}}
<a href="http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/0b4dd8dcf847440f9177825137c054ca.html">
<div>
      <canvas style="display: block" id="canvas_1fc2" width="800" height="800"></canvas>
      <script>
        var descent = new Descent(800, 800);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_1fc2'),
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/4b4fdd12-901e-4f10-a2cc-e9235bf5aae7.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/3ba37919-b3f2-4061-bd5d-bbcc6a9055ae.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/0aa4950c-017c-438c-af2d-9d7992b5d706.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/b669ce34-fb26-48c3-b3bb-3a33e89a8137.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/f7e0d573-2808-40f0-af4f-6c2ca8ef1958.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/5385677c-322f-43b9-a4c1-b8be0c601045.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/afa71374-324d-42e9-8a4c-6d845fa8f274.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/5fbd03ba-e87b-44c3-9615-28df5d281bb0.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/64118fc5-36c3-414d-98d6-ebc8c912b6c2.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/0395d332-da8c-4510-9f17-ce738fc4e23c.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/a69cf555-1200-492a-bc79-f0a9b4bb4c86.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/28f7b981-3066-4858-bd56-398eccb1e749.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/321c1b72-c329-4b02-a9c7-6befab0b6a5f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/f21dc431-7449-4e0f-8f07-3c7fa5cbefbd.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/4017a90f-1464-48c6-b17b-ff755e5a1591.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/6a35ed82-2193-4f55-b1cf-8f26e9f1be97.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/c498111f-bedf-4f79-ae6d-2973eeb8d14d.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/b9bf718d-891c-461e-a376-232e885c6f94.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/c47209bc-3c19-4e11-bf90-d7cabe7c139f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/c4af50a2-c6a1-442a-a50e-a8f20d9cf2bb.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/1d4f15d9-a5b8-4be7-9697-bf2ead12583f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/4501e858-ee1c-4369-916b-12fa30cc5a95.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/010c83de-f18e-4fcb-902d-eff5b50e6f5e.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/83890d64-8d8d-402f-9a3f-0fe5a0e8bc5d.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/5d37732e-029d-4b0f-a70e-7172f13ca1fb.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/c043f8aa-8d77-46fa-bbcb-922c89883016.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/e9df60ee-4649-4dd0-9327-895585ce99ed.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/98e0cfe8-0b08-4a8c-ac27-dd266dfb70c6.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/da4c8c87-d6ff-4458-904a-b6c345206793.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/8b3a4a57-298d-469a-a8bf-9e601b206708.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/d340b9ac-2d13-469b-977a-e84d237b2270.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/ac99a0e1-017c-420b-8a06-558154208fa9.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/3a9c1f4a-9fed-4324-b3a3-4a423ef3b647.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/5c24a418-c3dc-4330-8455-7c399288a16a.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/4a386ecd-1ca2-4ba2-81da-ac08576a6375.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/9b01d23d-3c72-41d3-945f-113c5ecefeee.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/4aab33f0-821d-4fa6-8003-6ba22c923db3.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/ee3fb3ad-ed1c-4bf2-8550-709a8cf456a3.jpg',
			'http://examples.deepartist.org/ZoomingRotor/403bcbb6-c201-4977-9443-fd2e3dcad384/etc/d586bda1-619b-4774-b323-f5c9be85c82d.jpg');
      </script>
    </div>
	</a>
{{< /rawhtml >}}
	
# 10

{{< rawhtml >}}
<a href="http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/ZoomingRotor.html">
<div>
      <canvas style="display: block" id="canvas_1754" width="800" height="800"></canvas>
      <script>
        var descent = new Descent(800, 800);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_1754'),
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/385f0848-f924-487f-b995-5e6e1ea36bf9.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/049e75a9-0359-4eb1-ae39-8b5c80e0f601.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/3eb51642-e915-4f27-acd6-d1582823c2e0.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/d74f65de-1687-40ab-a91c-603841d2e0ed.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/4ce6e53a-bdb5-4fca-b8af-1350eb3a04a0.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/a31285e4-2ac2-4da7-a04c-a425b66e5784.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/b4ef96e4-0f3e-4260-bbd4-c2f9cf51df0a.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/938b02c8-a251-4e84-b870-cfabc18b2663.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/feeeacc2-af73-4bf8-a91a-7418f6c2ec68.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/ca523bea-f305-4884-bbd8-51f2880705e0.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/742c9b18-f038-43ae-a595-63aa1762491f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/841659fd-869c-4cce-8a35-985fc5d425b8.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/9198c97f-80b3-4a07-a448-287d278ba64e.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/7013bde6-0da4-4881-b01b-66161be00ff5.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/42b06150-ca0e-4891-8ce2-a803af981c8a.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/f1f7cb56-e224-4c8b-9048-14ccf69357c2.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/2ce39b75-9d4f-4adb-94cc-0d4648079f49.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/47a4253c-e0dd-4253-ae6c-56b019987b16.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/e7a9d239-d50e-4dd7-b71a-afc09d0ba5d2.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/adcafa0e-d74c-4271-a448-6280406763e4.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/d686d68e-3650-4c41-9eca-d95b4921a69f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/3ce9989c-ab6b-4371-9c35-9513f20a357f.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/7608fefd-d6c6-4289-a720-d918a74a1d71.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/574c8f61-e772-4a82-9183-eaeff6e6485d.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/5a9f0e3f-66a3-472d-a6bb-50d6c17fac03.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/bc50c818-4570-486d-8a45-ad5fc75a9736.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/aa490d39-6535-4ec1-be29-a36d0b959623.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/7eb96b6a-a097-4a3a-8230-780c6372addb.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/b4d93eaf-67c5-4fed-af53-baef03cf2de4.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/aaaca3c4-3eb2-499d-ba7f-ea0e71bac1f1.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/ca2cfad0-ada9-4083-8705-bf617598199d.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/c7481ddf-deac-4602-8b95-bf723db574f6.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/175f51b1-1b38-4bd5-a99b-e0b609cb7545.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/89d2b254-66ba-4fcd-b607-1c724486543e.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/00455a3d-684f-4728-ae3d-82ef82e43aa5.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/588a5ca8-9e4b-4c60-a6a6-9814c40dd1ea.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/601213f6-466b-4e51-beac-2eb036fc4510.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/f020e414-8207-4e8e-9881-dc85a052d4f1.jpg',
			'http://examples.deepartist.org/ZoomingRotor/ccdee01e-ea2a-4c5d-9759-82d8d5c12040/etc/ee42e544-852a-4b56-9763-3f4aef00c017.jpg');
      </script>
    </div>
	</a>
{{< /rawhtml >}}
	
# 11	

{{< rawhtml >}}
<a href="http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/AutoZoomingRotor.html">
<div>
      <canvas style="display: block" id="canvas_352" width="1024" height="1024"></canvas>
      <script>
        var descent = new Descent(1024, 1024);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_352'),
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/8443a8a0-7a90-4c0b-935e-2f8899ac9b61.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/2cdf6c1e-651f-4e0f-a1d0-ba3aeea2763f.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/41e0a2ad-e25e-4fe8-b86e-8799d8b561b7.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/57ae3f26-9bd8-4e98-9de0-fea1a2c5b3da.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/48c448e9-9d6c-4031-b625-a380a50394ff.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/b1eaf6d9-1d43-45dd-901f-baf67ee6618f.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/154d64f4-9b36-4557-81ac-de9d5282b52f.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/ae11a090-3d99-480a-82bb-3a7394785458.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/bb2b59e6-a2fb-4377-aee8-b4691492b6ff.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/b15490f2-bcbf-444d-b1aa-460a4af5979c.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/a2b7eb38-e4be-4c08-8436-db22e20d0f61.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/42991ce9-d508-4f06-ba99-4be207ca1572.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/146b0faa-23f1-4d8f-8c98-5a54a54abb18.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/e2032958-2d5d-41ac-bfb4-3780aee20a2a.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/5de9674e-402c-45e6-bde2-4a0c633466e3.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/7efe512d-0134-48b0-a239-cbba3fbad9bd.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/109d82b2-cc9b-438c-aea0-6305a7802428.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/45fa84fb-9e07-40fd-b137-ad9ee0919b3e.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/9b835b09-2970-4799-ba21-d7b1b3502449.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/04146ed6-2941-45b2-81f6-fbdbab2e37d5.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/2b7f1e47-ba4b-4b4e-a076-84f7885de5c7.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/ffffbbb0-ff25-438f-80b8-1a8c202109c7.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/79e6db85-7944-4807-a88b-e6aada2cf8d7.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/4eca2565-21e7-402d-bf61-08de58a7800c.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/2872d1fd-5542-45d4-8bd6-70f53c39aed5.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/e2273177-d2d5-48f5-96c9-f73668408430.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/87c31a45-ec92-4cc4-ba52-addf49102931.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/b12d1a7a-a154-4935-a6f0-2d16fd7552c6.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/36a28542-2b29-4d89-aa77-1f189b5faec8.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/981cc80b-7852-40b5-ad0a-02e0846ac4e7.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/22aa7fa6-268c-40dc-acd7-32287021d5dd.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/cfc23129-0fc9-46db-b2bf-17cbd415fdf4.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/e889b4fe-a419-475a-bb25-b693d876a3bb.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/d5eabbf0-f493-4152-bcd1-b36086dcece4.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/96c585fc-a611-47a0-9f05-8dfc6de5d1c4.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/6d5340d4-af20-4aa6-a405-fa1a67a77575.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/887fe693-1973-4639-bce0-960c3f34c05f.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/210a39c2-17a4-400a-a330-d2e1c9b3b53e.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a98aef99-1b59-4a23-9664-311a789e27f2/etc/9385ad8d-2a8f-403a-8c56-b2a3bef7c69c.jpg');
      </script>
    </div>
	</a>
{{< /rawhtml >}}
	
# 13

{{< rawhtml >}}
<a href="http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/AutoZoomingRotor.html">
<div>
      <canvas style="display: block" id="canvas_c80" width="1200" height="1200"></canvas>
      <script>
        var descent = new Descent(1200, 1200);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_c80'),
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/7837f9e8-c831-461d-8693-f1857f5cfc12.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/503b2828-e703-4ae6-85bf-1eea17a7ecc9.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/8d088c7a-f896-4e66-a4d9-46fd61c97b67.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/6769ac94-f2ca-4097-9e54-a32983f37bb6.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/fff37473-8287-47c4-9446-ec4ba062532d.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/d9f72e10-3389-4b9f-a33e-f3e22ab5e0e1.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/46b54881-30ad-48da-8df5-6c9e497575a8.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/f7669dbd-4d10-4fa2-8cd6-d9d02804857d.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/1d0bd012-4b4d-4856-a1b0-2e68f0e3457b.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/490ac997-cd73-425f-8d7a-eefd521f2fdf.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/7265bdeb-79c2-4325-bf89-20d9959e3105.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/56b47a5a-bbf2-4d04-8900-df4492574d36.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/1e076c31-e7b3-4c1a-8cb9-bea676443887.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/5321c647-f77f-435c-af4a-f6cb42deaaae.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/a20597a6-bb05-4f9f-aea3-9a23270bf8a5.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/248ead35-a1aa-4dde-a0c0-7d99000716da.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/efb805a3-a8be-4085-8178-6f291718c31a.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/ed3c8b37-1309-469f-b691-e46620e4007e.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/6c9e9a9b-c5e2-4b2d-940e-b945da3fc809.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/a2ba89e9-8e6a-4953-a6a1-4a054f864765.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/6817e064-1529-4ba7-b9bf-95196ad87681.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/07859df8-cb6c-4a26-a924-b80deef4510c.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/2ebfc5d4-9b5e-4235-adb6-a5e9050eb5ae.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/832e72b2-8625-45e1-992f-97b8c2d119fc.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/c71a4b28-a96a-452d-94bb-4c70c59beca9.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/4192ccb9-2a59-4708-851d-8f58f336f2d5.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/0ecd8f5c-fd80-4c7a-b41b-f518655429c6.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/52827327-c0c8-48bf-8209-3f161febe61b.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/c1885b84-c9e1-4631-a8a1-442a0b17045f.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/b8365965-f7a8-49b2-8de4-82b5979fbd23.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/2e1fbecf-376d-4f3c-8ebe-8384d9eae1b1.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/7c4c387d-f0f9-4c0f-9652-4a45583c693c.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/64b578a2-3037-4cdc-bbef-13bf17943592.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/ec0c3311-20cf-4fbe-ac67-b2cd74e3d292.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/065bee52-d646-4f4c-92e4-ea61c5b89c43.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/f2db03a7-b09d-43c6-90c7-91708fcdc257.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/ac052947-87cf-44f6-b497-96f39d814c2c.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/36d91671-0f78-4687-9223-7c73c48c040d.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/a0810917-9bf5-477f-b827-1d589e67892d/etc/a31257aa-0880-48d8-b833-cd0a6b89d6a5.jpg');
      </script>
    </div>
	</a>
{{< /rawhtml >}}
	
# 14

{{< rawhtml >}}
<a href="http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/AutoZoomingRotor.html">
<div>
      <canvas style="display: block" id="canvas_1a8f" width="1200" height="1200"></canvas>
      <script>
        var descent = new Descent(1200, 1200);
		descent.stepZoom = 0.5;
		descent.animate(document.getElementById('canvas_1a8f'),
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/6767bac2-d944-4adb-b72c-9f277e9cf24d.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/78a359d8-2d1a-46f1-9bec-e514f2dfc047.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/b4b97d80-9b00-4b01-ae79-fb5feeb631b6.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/5a57f47c-5da7-45e6-b65d-f4328c20d4d9.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/cacb499e-6a86-4ce9-9e34-ef0a60839996.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/a8712e99-d6a7-4413-aab3-3ed837d54d2c.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/f00419af-0805-4bbc-9f68-30eef2c39195.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/283a8fdf-9df7-4fdb-9343-faaec8bfdcef.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/66000aa5-3dc1-4604-b651-c0a0eb2c3e9f.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/3fee1e91-6a38-479c-97b9-2320dd549493.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/d9e1f056-9308-441d-9d7f-acf9ddc83f0c.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/5bcef1fd-349b-4062-a8bd-4bae5dc4f15d.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/87c12d5f-29dd-44fe-9ae3-4d35174be1b9.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/cb3e2f74-c9b9-4073-a1e2-190afa390154.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/67e91783-6d76-4d73-bccf-e68562223b40.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/d95b2b41-9616-41de-9b24-c6e9b86918e8.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/59ba36a9-9c7a-4592-b8fe-d7e3964d27f9.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/d9debf72-0aa9-47dc-bc88-7c44b56b3b00.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/1b4839ff-b896-4387-a78b-b5e5f59febae.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/08e612e9-5e57-49d0-ab67-b11d751a0198.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/89e14b8b-b61d-4fd1-b616-49cac4923d64.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/afff1fa8-29fc-4ce4-b4bc-d4a3d219702d.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/596c2cca-6691-456a-bcb8-a4d78dba996a.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/c51ab759-6283-4de9-8216-f4a5dbaddf8f.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/ed20c93d-2c48-4bc9-b399-3cff24a2a204.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/02dfb7e0-20a1-4aac-a27e-9fa905234261.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/6ab4e755-fd6f-47f5-8bae-3e333b7fddd3.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/c3fcd787-77c9-43ce-b95c-3595f2aee627.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/20b00aad-9a52-416b-8f43-ffb3af2f2a5a.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/a9816734-0f3e-4804-bfeb-7a4ca5c311dd.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/11ffc25d-b13e-44fe-97a4-8891de2d94b9.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/7b190a20-fd2d-40f5-8bfe-786f3297633a.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/65c0037f-e030-434f-8290-5451169ce1fd.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/44a21107-0173-48c1-b657-4ef7a626042d.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/e67c0d52-0ab3-416a-9a39-89f0225433df.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/6bc9d11a-c352-46ba-bde8-3297a3e3be83.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/0bf8c1f7-8da5-4f01-aaef-480614ef26f1.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/628ccdce-1bec-4bc9-8f33-374e866387ed.jpg',
			'http://examples.deepartist.org/AutoZoomingRotor/41cbc853-83d4-4a32-9291-8969c27f99e1/etc/ebc4f5fb-7ca5-4181-bdb0-d5becb789752.jpg');
      </script>
    </div>
	</a>
{{< /rawhtml >}}
{{< rawhtml >}}

