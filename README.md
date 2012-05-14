delete-unused-steps
===================

Script to delete unused cucumber steps from step definitions.

Usage:

1. Run cucumber with the 'usage' format, redirecting the output to a file, e.g.
<pre>
     cucumber --format usage > cuke_output.txt
</pre>
or
<pre>
     bundle exec cucumber features/ --format usage > cuke_output.txt
</pre>
2. Truncate the beginning of the file, up to the unused steps listing; the resulting file should resemble this:    

<pre>

    0.0013150 /^I should see the Alien Attributes table with default values$/                                   # features/step_definitions/configuration/alien_view.rb:190
      NOT MATCHED BY ANY STEPS
    0.0000000 /^I should see my Life Force status \((\d+)\) in the Status Pane$/                              # features/step_definitions/configuration/base_steps.rb:190
      NOT MATCHED BY ANY STEPS

</pre>

3. Pipe the resulting truncated file to the script, e.g.:

    
    cat cuke_unused_steps.txt | script/delete_unused_steps


The script will delete the listed steps from their definition files.


*CAVEAT: Don't run the script against the untruncated output file, lest valid steps be excised!*

