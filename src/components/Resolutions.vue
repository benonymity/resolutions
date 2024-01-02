<template>
  <div class="resolutions">
    <div
      v-for="(resolution, index) in resolutions"
      :key="index"
      class="resolution"
      @click="copyToClipboard(resolution)"
    >
      <h1>{{ index + 1 }}</h1>
      <p>
        {{ resolution }}
      </p>
    </div>
    <div v-if="showToast" class="toast">Copied to clipboard</div>
  </div>
</template>

<style scoped>
p {
  font-size: 20px;
  line-height: 23px;
  font-family: serif;
}
h1 {
  padding-left: 10px;
  padding-right: 20px;
}
.toast {
  position: fixed;
  bottom: -100px;
  left: 50%;
  font-family: sans-serif;
  font-size: 15px;
  transform: translateX(-50%);
  background-color: rgba(0, 0, 0, 0.7); /* Opaque grey background */
  color: white;
  padding: 7px 12px;
  border-radius: 7px; /* Rounded corners */
  text-align: center;
  z-index: 1000; /* Ensures it's above other elements */
  animation:
    slideUp 0.2s forwards,
    slideDown 0.4s 2.1s forwards;
}
@keyframes slideUp {
  to {
    bottom: 20px; /* Adjust this value to control final position from bottom */
  }
}

@keyframes slideDown {
  from {
    bottom: 20px;
  }
  to {
    bottom: -100px; /* Moves back off screen */
  }
}
.resolutions {
  padding-bottom: 60px;
  position: relative;
}
@media screen and (max-width: 700px) {
  .resolutions {
    padding-bottom: 200px;
  }
}

.resolutions::before {
  content: "";
  position: sticky;
  display: block;
  top: 0;
  left: 0;
  right: 0;
  height: 30px; /* Adjust the height as needed */
  background: linear-gradient(to bottom, #fafafa, rgba(255, 255, 255, 0));
  z-index: 2;
}

.resolutions::after {
  content: "";
  position: sticky;
  display: block;
  top: 0;
  left: 0;
  right: 0;
  height: 30px; /* Adjust the height as needed */
  background: linear-gradient(
    to bottom,
    rgba(255, 255, 255, 1),
    rgba(255, 255, 255, 0)
  );
  z-index: 2;
}

.resolution {
  margin: 15px;
  padding: 10px;
  border: 2px solid black;
  border-radius: 10px;
  box-shadow: 2px 2px 2px gray;
  transition:
    opacity 0.4s,
    box-shadow 0.2s;
  background-color: #f0f0f0;
  /* background-image: url('https://static.vecteezy.com/system/resources/previews/006/397/031/non_2x/abstract-background-with-grunge-style-old-paper-texture-vector.jpg'); */
  display: flex;
  align-items: center;
  /* justify-content: center; */
  z-index: 1;
  position: relative;
}
.resolution:hover {
  box-shadow: 5px 5px 5px gray;
}
</style>

<script>
export default {
  data() {
    return {
      resolutions: [
        "That I will do whatsoever I think to be most to God’s glory, and my own good, profit and pleasure, in the whole of my duration, without any consideration of the time, whether now, or never so many myriad’s of ages hence. To do whatever I think to be my duty and most for the good and advantage of mankind in general. To do this, whatever difficulties I meet with, how many and how great soever.",
        "To be continually endeavoring to find out some new invention and contrivance to promote the aforementioned things.If ever I shall fall and grow dull, so as to neglect to keep any part of these Resolutions, to repent of all I can remember, when I come to myself again.",
        "Resolved, if ever I shall fall and grow dull, so as to neglect to keep any part of these Resolutions, to repent of all I can remember, when I come to myself again.",
        "Never to do any manner of thing, whether in soul or body, less or more, but what tends to the glory of God; nor be, nor suffer it, if I can avoid it.",
        "Never to lose one moment of time; but improve it the most profitable way I possibly can.",
        "To live with all my might, while I do live.",
        "Never to do anything, which I should be afraid to do, if it were the last hour of my life.",
        "To act, in all respects, both speaking and doing, as if nobody had been so vile as I, and as if I had committed the same sins, or had the same infirmities or failings as others; and that I will let the knowledge of their failings promote nothing but shame in myself, and prove only an occasion of my confessing my own sins and misery to God.",
        "To think much on all occasions of my own dying, and of the common circumstances which attend death.",
        "When I feel pain, to think of the pains of martyrdom, and of hell.",
        "When I think of any theorem in divinity to be solved, immediately to do what I can towards solving it, if circumstances don’t hinder.",
        "If I take delight in it as a gratification of pride, or vanity, or on any such account, immediately to throw it by.",
        "To be endeavoring to find out fit objects of charity and liberality.",
        "Never to do anything out of revenge.",
        "Never to suffer the least motions of anger to irrational beings.",
        "Never to speak evil of anyone, so that it shall tend to his dishonor, more or less, upon no account except for some real good.",
        "That I will live so as I shall wish I had done when I come to die.",
        "To live so at all times, as I think is best in my devout frames, and when I have clearest notions of things of the gospel, and another world.",
        "Never to do anything, which I should be afraid to do, if I expected it would not be above an hour, before I should hear the last trump.",
        "To maintain the strictest temperance in eating and drinking.",
        "Never to do anything, which if I should see in another, I should count a just occasion to despise him for, or to think any way the more meanly of him.",
        "To endeavor to obtain for myself as much happiness, in the other world, as I possibly can, with all the power; might, vigor, and vehemence, yea violence, I am capable of, or can bring myself to exert, in any way that can be thought of.",
        "Frequently to take some deliberate action, which seems most unlikely to be done, for the glory of God, and trace it back to the original intention, designs and ends of it; and if I find it not to be for God’s glory, to repute it as a breach of the 4th Resolution.",
        "Whenever I do any conspicuously evil action, to trace it back, till I come to the original cause; and then both carefully endeavor to do so no more, and to fight and pray with all my might against the original of it.",
        "To examine carefully, and constantly, what that one thing in me is, which causes me in the least to doubt of the love of God; and to direct all my forces against it.",
        "To cast away such things, as I find do abate my assurance.",
        "Never willfully to omit anything, except the omission be for the glory of God; and frequently to examine my omissions.",
        "To study the Scriptures so steadily, constantly and frequently, as that I may find, and plainly perceive myself to grow in the knowledge of the same.",
        "Never to count that a prayer, nor to let that pass as a prayer, nor that as a petition of a prayer, which is so made, that I cannot hope that God will answer it; nor that as a confession, which I cannot hope God will accept.",
        "To strive to my utmost every week to be brought higher in religion, and to a higher exercise of grace, than I was the week before.",
        "Never to say anything at all against anybody, but when it is perfectly agreeable to the highest degree of Christian honor, and of love to mankind, agreeable to the lowest humility, and sense of my own faults and failings, and agreeable to the golden rule; often, when I have said anything against anyone, to bring it to, and try it strictly by the test of this Resolution.",
        "To be strictly and firmly faithful to my trust, that that in Prov. 20:6, “A faithful man who can find?” may not be partly fulfilled in me.",
        "Always to do what I can towards making, maintaining, establishing and preserving peace, when it can be without over-balancing detriment in other respects.",
        "In narrations never to speak anything but the pure and simple verity.",
        "Whenever I so much question whether I have done my duty, as that my quiet and calm is thereby disturbed, to set it down, and also how the question was resolved.",
        "Never to speak evil of any, except I have some particular good call for it.",
        "To inquire every night, as I am going to bed, wherein I have been negligent, what sin I have committed, and wherein I have denied myself: also at the end of every week, month and year.",
        "Never to speak anything that is ridiculous, sportive, or matter of laughter on the Lord’s day.",
        "Never to do anything that I so much question the lawfulness of, as that I intend, at the same time, to consider and examine afterwards, whether it be lawful or no; except I as much question the lawfulness of the omission.",
        "To inquire every night, before I go to bed, whether I have acted in the best way I possibly could, with respect to eating and drinking.",
        "To ask myself at the end of every day, week, month and year, wherein I could possibly in any respect have done better.",
        "Frequently to renew the dedication of myself to God, which was made at my baptism; which I solemnly renewed, when I was received into the communion of the church; and which I have solemnly re-made this twelfth day of January, 1722-23.",
        "Never henceforward, till I die, to act as if I were any way my own, but entirely and altogether God’s, agreeable to what is to be found in Saturday, January 12, 1723.",
        "That no other end but religion, shall have any influence at all on any of my actions; and that no action shall be, in the least circumstance, any otherwise than the religious end will carry it.",
        "Never to allow any pleasure or grief, joy or sorrow, nor any affection at all, nor any degree of affection, nor any circumstance relating to it, but what helps religion.",
        "Never to allow the least measure of any fretting uneasiness at my father or mother. To suffer no effects of it, so much as in the least alteration of speech, or motion of my eve: and to be especially careful of it, with respect to any of our family.",
        "To endeavor to my utmost to deny whatever is not most agreeable to a good, and universally sweet and benevolent, quiet, peaceable, contented, easy, compassionate, generous, humble, meek, modest, submissive, obliging, diligent and industrious, charitable, even, patient, moderate, forgiving, sincere temper; and to do at all times what such a temper would lead me to. ",
        "Constantly, with the utmost niceness and diligence, and the strictest scrutiny, to be looking into the state of my soul, that I may know whether I have truly an interest in Christ or no; that when I come to die, I may not have any negligence respecting this to repent of.",
        "That this never shall be, if I can help it.",
        "I will act so as I think I shall judge would have been best, and most prudent, when I come into the future world.",
        "That I will act so, in every respect, as I think I shall wish I had done, if I should at last be damned.",
        "I frequently hear persons in old age say how they would live, if they were to live their lives over again: that I will live just so as I can think I shall wish I had done, supposing I live to old age.",
        "To improve every opportunity, when I am in the best and happiest frame of mind, to cast and venture my soul on the Lord Jesus Christ, to trust and confide in him, and consecrate myself wholly to him; that from this I may have assurance of my safety, knowing that I confide in my Redeemer.",
        "Whenever I hear anything spoken in conversation of any person, if I think it would be praiseworthy in me, I will endeavor to imitate it.",
        "To endeavor to my utmost to act as I can think I should do, if I had already seen the happiness of heaven, and hell torments.",
        "Never to give over, nor in the least to slacken my fight with my corruptions, however unsuccessful I may be.",
        "When I fear misfortunes and adversities, to examine whether I have done my duty, and resolve to do it; and let it be just as providence orders it, I will as far as I can, be concerned about nothing but my duty and my sin.",
        "Not only to refrain from an air of dislike, fretfulness, and anger in conversation, but to exhibit an air of love, cheerfulness and benignity.",
        "When I am most conscious of provocations to ill nature and anger, that I will strive most to feel and act good-naturedly; yea, at such times, to manifest good nature, though I think that in other respects it would be disadvantageous, and so as would be imprudent at other times.",
        "Whenever my feelings begin to appear in the least out of order, when I am conscious of the least uneasiness within, or the least irregularity without, I will then subject myself to the strictest examination.",
        "That I will not give way to that listlessness which I find unbends and relaxes my mind from being fully and fixedly set on religion, whatever excuse I may have for it-that what my listlessness inclines me to do, is best to be done, etc.",
        "Never to do anything but duty; and then according to Ephesians 6:6-8, do it willingly and cheerfully as unto the Lord, and not to man; “knowing that whatever good thing any man doth, the same shall he receive of the Lord.”",
        "On the supposition, that there never was to be but one individual in the world, at any one time, who was properly a complete Christian, in all respects of a right stamp, having Christianity always shining in its true luster, and appearing excellent and lovely, from whatever part and under whatever character viewed: Resolved, to act just as I would do, if I strove with all my might to be that one, who should live in my time.",
        "When I find those “groanings which cannot be uttered” (Romans 8:26), of which the Apostle speaks, and those “breakings of soul for the longing it hath,” of which the Psalmist speaks, Psalm 119:20, that I will promote them to the utmost of my power, and that I will not be weary of earnestly endeavoring to vent my desires, nor of the repetitions of such earnestness.",
        "Very much to exercise myself in this all my life long, viz. with the greatest openness I am capable of, to declare my ways to God, and lay open my soul to him: all my sins, temptations, difficulties, sorrows, fears, hopes, desires, and every thing, and every circumstance.",
        "Resolved, that I will endeavor always to keep a benign aspect, and air of acting and speaking in all places, and in all companies, except it should so happen that duty requires otherwise.",
        "Resolved, after afflictions, to inquire, what I am the better for them, what good I have got by them, and what I might have got by them.",
        "To confess frankly to myself all that which I find in myself, either infirmity or sin; and, if it be what concerns religion, also to confess the whole case to God, and implore needed help.",
        "Always to do that, which I shall wish I had done when I see others do it.",
        "Let there be something of benevolence, in all that I speak.",
      ],
      showToast: false,
    };
  },
  methods: {
    async copyToClipboard(resolutionText) {
      try {
        await navigator.clipboard.writeText("Resolved: " + resolutionText);
        this.showToast = true;
        setTimeout(() => {
          this.showToast = false;
        }, 2500);
      } catch (err) {
        console.error("Failed to copy: ", err);
      }
    },
  },
};
</script>
