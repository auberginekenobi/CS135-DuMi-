# DuMI DB Notes

Kelli's notes for db-mapper/kelli branch. Contains references, issues, plans, etc.

### Du Class variable reference:
```php
	protected $du_id;               // [string]          The du's du_id
	protected $du_timestamp;        // [string]          The timestamp recorded for the du
	protected $du_name;             // [string]          The name recorded for the du
	protected $du_has_date;         // [boolean]         If the du is linked to a date
	protected $du_has_deadline;     // [boolean]         If the du is linked to a deadline
	protected $du_has_duration;     // [boolean]         If the du is linked to a start and end time
	protected $du_time_start;       // [string]          Deadline or start time of the du, if it has one
	protected $du_time_end;         // [string]          End time of the du, if it has one
	protected $du_priority;         // [int]             Priority recorded for the du
	protected $du_enforce_priority; // [boolean]         If the du has been set to a priority
	protected $tag_priorities;      // [array(int)]      Priorities specifications for each tag recorded for the du
	protected $calc_priority;       // [int]             Priority calculated for the du
	protected $du_note;             // [string]          The note recorded for the du
	protected $du_tags;             // [array(string)]   Tags recorded for the du
```

### Todo
1. update setThing descriptions // db-class.php
2. create addDu, editDu function // db-mapper.php
3. make tag class
4. make status class

public function setDuPriority($du_priority) {
	global $log;
	$olddate = ($this->du_has_date) ? substr($this->du_time_start, 0, 10) : NULL;
	if (query($updateQuery, "setDuPriority()") === TRUE) {
		$output .= $this->du_id . " successfully: ";
		$output .= ($olddate) ? "changed date from '" . $olddate . "' to '" . $justdate . "'.\n" :
							    "linked date '" . $justdate . "'.\n";
	}
}