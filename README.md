# Location

use_bpm 142
i = 0
use_synth :piano
wake = "C:/Users/Luis Rios/Documents/Audacity/sound effect wake up fl1thy.wav"
control ="C:/Users/Luis Rios/Documents/Audacity/control.wav"
wha = "C:/Users/Luis Rios/Documents/Audacity/Playboi Carti - WHAT Sound Effect-Adlib.wav"
yeat = "C:/Users/Luis Rios/Documents/Audacity/Yeat Interview.wav"
molly = "C:/Users/Luis Rios/Documents/Audacity/Playboi Carti - Molly (sped up).wav"

use_bpm 142
i = 0
use_synth :piano
notes = [ :e5, :d5, :c5, :b4, :c5, :d5, :e5, :e5, :d5, :c5, :b4, :r]
live_loop :main do
  20.times do
    12.times do
      play notes[i],release: 0.2
      sleep 0.25
      i = i + 1
    end
    sleep 1
    i = 0
  end
  stop
end

sleep 12

z = 1
define :wakey do |a,b,c|
  1.times do
    4.times do
      if z == 1
        sample wake, start: a, finish: b, amp: c
        sleep 0.5
      elsif z <= 4
        sample goat, start: a, finish: b, amp: c
        sleep 0.5
      end
      z = z + 1
    end
    z=1
  end
end

wakey 0,0.1,1
wakey 0.1,0.2,2
wakey 0.2,0.3,3


sleep 4
live_loop :drums1 do
  40.times do
    sample :drum_heavy_kick, amp: 2
    sleep 1
  end
  stop
end

sleep 4

live_loop :kitty do
  15.times do
    sample :perc_bell2
    sleep 4
  end
  stop
end

n = 1
define :selection do |a|
  live_loop :samps do
    
    if n == 1
      sample wha, amp: a
      sleep 4
    elsif n < 3
      sample yeat
      sleep 4
    else
      print ("Jump out the show")
      stop
    end
    sleep 1
    n = n + 1
  end
end

selection 4

sleep 10

wakey 0.3,1,4
wakey 0.2,0.3,3
wakey 0.1,0.2,2
wakey 0,0.1,1

sleep 20

sample molly
